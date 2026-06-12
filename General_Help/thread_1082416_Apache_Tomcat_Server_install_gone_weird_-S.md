---
title: "Apache Tomcat Server install gone weird :-S"
date: 2009-02-27
forum: General Help
---

### Post by mattgaunt on 2009-02-27
Hey everyone

I've been trying to install tomcat into the directory /home/matt/Sites/tomcat/ and not having much luck, I managed to install it in /etc/local/tomcat/ but this folder hasn't seems to work.

The main problem is that when i now log into localhost:8080/ rather than get the tomcat index page, I get the following message:

Motion 3.2.9 Running [1] Threads
All

And when i log into localhost:8081 I get a shot of my webcam :-S which i didnt set up at all

Does anyone have any idea how to get rid of the webcam thing and get tomcat on the port 8080?

I think this is the problem as cataline.out (Error log from tomcat) has this message

java.net.BindException: Address already in use<null>:8080

Cheers
Matt

---

### Post by mattgaunt on 2009-02-27
Ok i managed to fix my own problem hee hee

I ended up using the command:

killall motion

then running th startup.sh script in the tomcat directory and everything fixed itself, Im just confused as to why motion started in the first place :-S

---

