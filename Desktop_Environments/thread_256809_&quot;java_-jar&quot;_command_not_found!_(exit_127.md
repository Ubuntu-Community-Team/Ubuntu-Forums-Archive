---
title: "&quot;java -jar&quot; command not found! (exit 127)"
date: 2006-09-13
forum: Desktop Environments
---

### Post by Toub on 2006-09-13
Hi,

I can not run java from command-line:

22:27 toub@pc1 ~/Desktop% java -jar jboss-installer.jar
zsh: command not found: java
zsh: exit 127   java -jar jboss-installer.jar

:confused: 

My jar file has full rights.
22:27 toub@pc1 ~/Desktop% ls -l jboss-4.0.4.GA-Patch1-installer.jar
-rwxrwxrwx 1 toub toub 59M 2006-09-13 21:48 jboss-installer.jar*

Does somebody know what's going wrong here?

What about Java on my Ubuntu 6.06 OS? : 
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
*     3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java


:KS Any idea? Thanks for your help!

---

### Post by Toub on 2006-09-13
If I launch the jar graphically using the mouse with 'Sun java 5 runtime", it works.

Why does it not from the command line?

---

### Post by lamego on 2006-09-13
Read
[https://help.ubuntu.com/community/Java/](https://help.ubuntu.com/community/Java/)

Specially the java link update instruction:
```
sudo update-java-alternatives -s java-1.5.0-sun
```

---

### Post by Toub on 2006-09-16
Yes, it was the problem.

I execute the following line and all is ok now:

sudo update-java-alternatives -s java-1.5.0-sun



Thanks

---

