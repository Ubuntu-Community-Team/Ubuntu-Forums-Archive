---
title: "jGRASP and javac path????"
date: 2005-11-07
forum: Desktop Environments
---

### Post by toxic on 2005-11-07
Hey all.

I have been using linux for a while now and just switch to Ubuntu. I am very satified with Ubuntu:) .

Well my problem is that I am lerning java in school and we are using jGRASP as IDE. I have installed the jdk with NetBeans in /opt .

I am able to run and compile java app. in NetBeans but in jGRASP I am able to run but not compile. When I compile I get this error.

 ----jGRASPexec:javac-g/home/toke/HA(dat)/3.Semester/it2/java/opgave_1_2/opgave_1_3.java
 ----jGRASP wedge: could not execute  javac
 ----   error number 2.
 ----   
 ----   Target does not exist or is not on PATH.
 ----   Make sure you have the full JDK (J2SE SDK or other), /us/u/usr/games/javac
 ----   
 ----PATHis:/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games:".

 ----jGRASP: operation complete.


another thing is that I have look around in this forum and found a help to make a path in the /etc/profile

I added 

PATH=${PATH}:/opt/jdk1.5.0_04/bin/;

So now I am able to write $ java programe.java instead of /opt/jdk*/bin/java program.java

but I can't compile with $ javac I have to write to whole path /opt/jdk*/javac program

why is that???

hope someone can help me with both questions.

---

### Post by peixe on 2005-11-07
i have a similiar problem.

When i do "whereis javac"

i get:  whereis javac
javac:

can someone help us?

---

