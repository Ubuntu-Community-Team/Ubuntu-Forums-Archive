---
title: "Problem with Konqueror + Java after upgrade"
date: 2007-10-18
forum: Desktop Environments
---

### Post by Goliash on 2007-10-18
I upgrade from Feisty to Gutsy. Everything seems to be working but I have a problem with Java in Konqueror. I can see an attempt to load applet but finally I see "Applet Failed". Java works in Firefox and Netbeans. Version of Java: sun-java5-plugin 1.5.0-13-0ubuntu1

---

### Post by mattpker on 2007-10-18
Did you try reinstalling java? Let me know how it gose.

---

### Post by Goliash on 2007-10-19
I'have tried to reinstall java5, then I installed java6 but still the same problem. Java 6 in Firefox works.

---

### Post by chris00 on 2007-10-19
Is gij installed? If so, try uninstalling that. It stopped Eclipse working for me.

---

### Post by Goliash on 2007-10-19
Gij-4.1 and gij-4.2 are installed. Don't you know how I can show Java console? The checkbox isn't in Konqueror anymore. When I set path for Java to /usr/lib/jvm/java-6-sun-1.6.0.03/bin/java, it writes  Loading Applet, but nothing more.

---

### Post by Goliash on 2007-10-19
After uninstallation of gij the problem remains.

---

### Post by SimonJones on 2007-10-20
Go to the Settings of Konqueror, and in the Java section untick use KIO.

Solved my problem, after much headaches.

---

### Post by Goliash on 2007-10-20
It helped. Thanks.

But it seems to me applets are loading very long time :-(

---

### Post by Goliash on 2007-10-21
I don't understand this problem: Now when I go to website with Java applet in Konqueror and in Firefox (both the same problem), I have to wait more than 2 minutes and after that time it loads. I have already tried to uninstall (and install again) all java packages (apt-get purge), but it didn't help.
```
sun-java6-bin 
sun-java6-demo
sun-java6-doc  
sun-java6-fonts     
sun-java6-jdk             
sun-java6-jre                 
sun-java6-plugin
```
 I have installed those packages and I am using Kubuntu 7.10. 
After those 2 minutes I can browse through other applets and they load almost imediatelly. After closing and reopening firefox or konqueror the situation repeats :(

---

