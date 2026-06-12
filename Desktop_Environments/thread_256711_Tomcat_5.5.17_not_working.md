---
title: "Tomcat 5.5.17 not working"
date: 2006-09-13
forum: Desktop Environments
---

### Post by popcorn09 on 2006-09-13
Hi,

I installed tomcat and I am able to start it but if I open firefox and type [http://localhost](http://localhost), I get "Unable to connect. Firefox can't establish a connection to the server at localhost."

I have set the port to 80 in server.xml 
I followed the instructions on this page -> [http://ubuntuforums.org/showthread.php?t=44006&highlight=tomcat](http://ubuntuforums.org/showthread.php?t=44006&highlight=tomcat)

When i do a ps -aux | grep tomcat, I can find processes running. Yet I am not able to connect. My /etc/hosts files has the loopback IP address also.

Please help!!!!

Thanks.

---

### Post by popcorn09 on 2006-09-13
Well, I was supposed to start it with sudo. It works. :mad:

---

