# xml-documents

# XLink

In HTML we use anchor tags to create hyperlinks. On the same lines we can create hyperlinks in an XML document using
XLink. With XLink we can define two types of link : simple and extended. Simple links are links similar to HTML links and extended links are used for linking multiple resources together.

# XPointer
XPointer allows us to navigate to specific parts of an XMl document.

#XLink Syntax
In HTML we have to create a hyperlink. XML does not use any predefined tags to create hyperlinks. We can use any tag to create a hyperlink however we need to add a little bit of information to the tag to change it from a normal XML node to an XML hyperlink node. Lets look at an example:
<?xml version="1.0"?>
<bookstore xmlns:xlink="http://www.w3.org/1999/xlink">
	<book xlink:type="simple" xlink:href="http://www.lordoftherings.com">Lord of the rings</homepage>
	<book xlink:type="simple" xlink:href="http://www.harryporter.com">Harry Porter</homepage>
</homepages>
The most important thing to notice here is usage of the xmlns element. For XLink the namespace is http://www.w3.org/1999/xlink. Without this declartion we can’t use XLink in the document.
Next we can see two XLink attributes : xlink:type and xlink:href. The type element refers to the type of the hyperlink (Simple or Extended) and href refers to the location to which this link should navigate to.

# XPointer Syntax
Sometimes it is useful to navigate to specific areas of the same page. In HTML it is possible to do this using the # character. In XML we can achieve the same by using XPointers. To navigate to a specific part of a page we need to add a pound sign # and a XPointer expression after the URL in the xlink:href. Lets look at an example :
The target XML document is employees.xml

<?xml version="1.0" encoding="ISO-8859-1"?>
<employees>
	<employee id="17452" vertical="banking">
		<id>17452</id>
		<name>Jason</name>
		<experience>2</experience>
		<salary>35000</salary>
	</employee>

	<employee id="14782" vertical="insurance">
		<id>14782</id>
		<name>Jim</name>
		<experience>3</experience>
		<salary>45000</salary>
	</employee>

	<employee id="12563" vertical="telecom">
		<id>12563</id>
		<name>Charles</name>
		<experience>4</experience>
		<salary>55000</salary>
	</employee>
</employees>
The following XML document refers to employees in employees.xml using xlink and xpointers
<?xml version="1.0" encoding="ISO-8859-1"?>
<myemployees xmlns:xlink="http://www.w3.org/1999/xlink">
	<myemployee xlink:type="simple"
		xlink:href="employees.xml#14782">
		<description xlink:type="simple"
			Jim is the employee of the year
		</description>
	</myemployee>
</myemployees>

# Explanation
In the example above we navigate to employee node with id=14782. This can be done by using either of the forms of XPointer :
•	xlink:href=”employees.xml#xpointer(id(’14782′))”
•	xlink:href=”employees.xml#14782
Both of these forms result in the same output and can be used interchangeably.
