---
title: "eclipse wont start confusion"
date: 2006-09-18
forum: Desktop Environments
---

### Post by T*&amp;1p87)v# on 2006-09-18
Hi,

after a lot of surfing trying to resolve my problem which seemed to be harmless I finally decided to ask for help personally.

Here is the deal, I downloaded eclipse and sun's java 1.5 using synaptic and isntalled everything, but when I tried to run eclipse I got an error which was very similar to what you will see later in this post. Then I decided to download everything manually, so I went to sun's  page and downloaded java SDK 1.5 + netebeans and stuff, also downloaded eclipse 3.2 and installed them locally in my home folder, set up the PATH to point to the new java, also set up the $JAVA_HOME. Oh and of course I removed everything from synaptic concerning eclipse and the sun's java.

after that the same error occurs:

JVM terminated. Exit code=1
/home/ayarov/bin/progs/jdk1.5.0_06/bin/java
-Xms40m
-Xmx256m
-jar /home/ayarov/bin/progs/eclipse/./startup.jar
-os linux
-ws gtk
-arch x86
-launcher /home/ayarov/bin/progs/eclipse/./eclipse
-name Eclipse
-showsplash 600
-exitdata 2c328005
-vm /home/ayarov/bin/progs/jdk1.5.0_06/bin/java
-vmargs
-Xms40m
-Xmx256m
-jar /home/ayarov/bin/progs/eclipse/./startup.jar 


strange!!! I searched in the net for this error, and the closest to the solution I got was 

java -jar ECLIPSEHOME/startup.jar

which unfortunately got me to 

*** glibc detected *** double free or corruption (out): 0x08bf7128 ***
Aborted

which totally confused me. Any ideas  out there??

Just to add smth here: Netbeans starts like a charm and I can develope using it, but I need eclipse :(

---

