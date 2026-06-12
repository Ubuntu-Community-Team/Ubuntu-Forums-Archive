---
title: "How to do something with Java"
date: 2005-12-12
forum: General Help
---

### Post by SomethingTohide on 2005-12-12
I've set this using
sudo update-alternatives config--java

but how do I set what to use as the compiler, it's not using JDK

cam@ubuntu:~$ sudo update-alternatives --config java

There are 6 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
      3        /usr/lib/j2re1.5-sun/bin/java
*     4        /usr/lib/j2sdk1.5-sun/bin/java
      5        /usr/bin/java-sablevm
      6        /etc/alternatives/kaffe-system/bin/java

Press enter to keep the default[*], or type selection number:
cam@ubuntu:~$

---

### Post by pertti on 2005-12-12
[QUOTE=SomethingTohide]I've set this using
sudo update-alternatives config--java

but how do I set what to use as the compiler, it's not using JDK[/QUOTE]

Try using:

sudo update-alternatives --config javac

I only have one javac installed (the one from Sun's Java), so it tells me that there is nothing to change, but this might not be your case.

---

