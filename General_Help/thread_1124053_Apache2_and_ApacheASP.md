---
title: "Apache2 and Apache::ASP"
date: 2009-04-13
forum: General Help
---

### Post by cjtjamandra on 2009-04-13
I have successfully installed Apache::ASP using this:


```
sudo apt-get install libapache2-mod-perl2
```


i have inserted this line of codes in the httpd.conf:

```
 PerlModule  Apache::ASP
 <Files ~ (\.asp)>
   SetHandler  perl-script
   PerlHandler Apache::ASP
   PerlSetVar  Global .
   PerlSetVar  StateDir /tmp/asp
 </Files>

```

i have restart apache successfully.


The problem appears when i try to open an asp page containing this:

```
<%
Response.Write("123")
%>
```

I am getting this error:


```

Internal Server Error
The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.


```

All asp pages are getting this error.


i opened the apache error.log and it shows this error:

```
[Mon Apr 13 12:01:54 2009] [error] [asp] [16324] [error] error compiling x.asp: syntax error at x.asp line 3, at EOF <-->
```


Please help. thanks.

---

### Post by cjtjamandra on 2009-04-13
No one has encountered this?.....

---

