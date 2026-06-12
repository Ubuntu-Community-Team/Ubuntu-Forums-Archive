---
title: "connecting tomcat to a database to query through jsp"
date: 2009-03-26
forum: General Help
---

### Post by Shpongle on 2009-03-26
i have tomcat installed and it works fine except it wont work offline:confused: for some reason but when connected to the net it works and processes scriplets and jsp pages, i set it up following this guide

[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/)

changing the version to 6.0.18 where appropriate, 


im trying to set up a database and make a connection to it, in college we are using ms access and we can set the jdbc odbc bridge through control panel,


iv been messing around for ages trying to get tomcat to connect to open office database / my sql server but to no avail, its the first time iv used them. so im not sure if im setting them up correct.

i can use any database, so if your familiar with another one and have got it working please let me know. . eg oracle or something
 

heres example code im trying to run

heres the html page to search the query


```
<html>

	<head>

	<title>search database</title>

	</head>



	<body>

	enter information about the person your looking for

	<form action="find.jsp" method="post">

		<table>

		<tr>

			<td>First Name:</td>

			<td><input type ="text" name ="fname"></td>

		</tr>

		<tr>

			<td>Surname:</td>

			<td><input type ="text" name ="sname"></td>

		</tr>

		<tr>

			<td>Password:</td>

			<td><input type ="password" name ="pword"></td>

		</tr>

		</table>

		<input type = "submit" value="submit">

	</form>



	</body>



</html>
```


heres the find.jsp page to query and forward to the list.jsp page
```
<%@ taglib prefix= "sql" uri="http://java.sun.com/jsp/jstl/sql" %>



<sql:setDataSource var ="labDb" scope = "session" driver = "sun.jdbc.odbc.JdbcOdbcDriver" url = "jdbc:odbc:labDb"/>

	

<sql:query var="lablist" scope="request" dataSource="${labDb}">

select * from Users

WHERE FirstName LIKE ?

AND SurName LIKE ?

AND PassWord LIKE ?

ORDER BY SurName

<sql:param value="%${param.fname}%"/>

<sql:param value="%${param.sname}%"/>

<sql:param value="%${param.pword}%"/>

</sql:query>

<jsp:forward page="list.jsp"/>





```


and heres the list page to display the queried results

```
<%@ taglibprefix="c" uri="http://java.sun.com/jsp/jstl/core" %>

<%@ taglibprefix="sql" uri="http://java.sun.com/jsp/jstl/sql" %>



<html>



<head>

	<title>list.jsp</title>

</head>



<body>

	<c:choose>

		<c:when test="${lablist.rowCount== 0}">Sorry, no people were found.</c:when>

	<c:otherwise>

	The following people were found:<p>

		<table border="1">

			<th>First Name</th>

			<th>Surname</th>

			<th>Password</th>

	<c:forEach items="${lablist.rows}" var="row">

			<tr>

			<td><c:out value="${row.FirstName}" /></td>

			<td><c:out value="${row.SurName}" /></td>

			<td><c:out value="${row.PassWord}" /></td></tr>

	</c:forEach>

		</table>

	</c:otherwise>

	</c:choose>

</body>



</html>

```



where labDB is the database name



any help is highly appreciated

---

### Post by Shpongle on 2009-03-26
if the database is needed for reference i can make it and take a screenshot

---

### Post by Shpongle on 2009-03-27
bump

---

### Post by Shpongle on 2009-03-27
any ideas anyone?

---

