---
title: "CGI cant write to file"
date: 2009-02-24
forum: General Help
---

### Post by mharvey87 on 2009-02-24
Hi I have a cgi script written in python that is in my home directory.
When I run the script in a browser I get an I/O error telling me the
script does not have permission to change the target file that is also in my home directory. The file has write permission for owner and group.
Another thing is if I run the script by itself outside of a browser then I writes to the file successfully.
Why won't it let the cgi script write to this file?

---

### Post by protodog on 2009-02-24
Are you running Apache?

If you are read this: [Apache Tutorial: Dynamic Content with CGI]("http://httpd.apache.org/docs/1.3/howto/cgi.html").

> Remember that the server does not run as you. That is, when the server starts up, it is running with the permissions of an unprivileged user - usually ``nobody'', or ``www'' - and so it will need extra permissions to execute files that are owned by you. 

---

### Post by mharvey87 on 2009-02-24
hey, thanks alot

---

