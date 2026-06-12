---
title: "Tomcat 6.0 on Ubuntu"
date: 2009-06-21
forum: Desktop Environments
---

### Post by hasatmax on 2009-06-21
Ok, I am a totally newbie at this..I want to implement web service on ubuntu (which runs on VMware) using tomcat server. Now that I have my tomcat server running (i.e., [http://localhost:8080/](http://localhost:8080/) gives a success web page !) I am stuck to how to go about 
the source code i have,(I know it sounds really silly but I am totally newbie to webservices and as a student I wish to experience how things work here) I have one "client" directory and a "tomcat-webapps" directory. Now that coding is done I just want to implement this on my ubuntu 8.10 using tomcat 6.0. Could any one kindly take pains 
to give out steps which i need to try to implement the work I have done so far.I know 
Note: The code is working fine, no errors in it.(java code) and tomcat is freaking me out. I hoped I would do something productive  this summer,plz help me here in the final stage..!!

Thanks.
Hasatmax.:)

---

### Post by hasatmax on 2009-06-22
kindly help any one..!!

---

### Post by _ric_ on 2009-07-06
Try running a sample app that comes with tomcat. You may need to install the tomcat6-docs package.
Go to the section "3) First webapp"[1] in the main documentation page. In the list of contents the last entry says "Example App"[2]. Go there and follow the instructions.

Basically you'll have to save the file "sample.war" in the webapps dir.

The problem that I was having is that I was using /usr/share/tomcat6 since the "It works!" page indicates that this is CATALINA_HOME and this is what I was using to test sample.war.

But it never worked for me. So I copied the file sample.war to /var/lib/tomcat6/webapps and it worked!

Try using /var/lib/tomcat6/webapps.

BTW, I using tomcat6 with Ubuntu 9.02 but I assume that the setup is the same.

Hopefully you'll find this helpful. I'm still trying to get my app to run so this is all I can help you with.

Good luck.

[1] [http://localhost:8080/docs/appdev/index.html](http://localhost:8080/docs/appdev/index.html)
[2] [http://localhost:8080/docs/appdev/sample/](http://localhost:8080/docs/appdev/sample/)

---

