---
title: "Web Server find"
date: 2008-03-07
forum: Education &amp; Science
---

### Post by mthalis on 2008-03-07
In my machine web server running but i don't know what it is,how can i find it.now i install xammp but it not work because previous web server running i want to find and remove previous sever.how can i do it.I use 7.10

---

### Post by r4e on 2008-03-08
To find out what web server is binding to port 80, run the following command and post the output here:

sudo netstat -plnt | grep :80

---

