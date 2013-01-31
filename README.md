# Declarative Support for Spring Environments in XML

Like @PropertySource, but in XML

# Example

    <environment:property-source location="classpath:foo.properties"/>

# Attributes

 *  id

    Optionally specifies the bean name, which is then used as the property
    source name. If you don't specify a name an automatically generated name
    will be used.

 *  location

    The only required attribute, specifying the location or locations of the
    resources to load. Multiple locations can be specified separated by a
    comma.

 *  order

    Allows ordering of property sources loaded into the environment independent
    of the source ordering in the XML. Defaults to 0. Property sources
    specified with higher order values are loaded later, and thus have a higher
    precedence.

 *  ignore-resource-not-found

    Allows loading of resources which may not be present at runtime. Defaults
    to `false`, which will cause an exception to be thrown if the resource is
    not found.

# Why

The existing `<context:property-placeholder />` namespace support causes
a bean factory post processor to run _for every placeholder registered_.
This has a side effect when multiple property sources are required, and
the placeholders in the XML specify a default value.

When the first bean factory post processor is executed, the properties
specified in resources loaded later are obviously not available. This results
in the default value being incorrectly substituted.

This issue has been raised but there's currently no out of the box support
from SpringSource to work around this. See 
[SPR-9989](https://jira.springsource.org/browse/SPR-9989).
 
# License

Copyright (c) 2013 Paul Tomlin

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
