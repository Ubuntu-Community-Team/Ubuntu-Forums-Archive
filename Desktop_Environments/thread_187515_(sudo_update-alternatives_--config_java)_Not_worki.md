---
title: "(sudo update-alternatives --config java) Not working"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Demon012 on 2006-06-03
Hi guys when I try to use

> sudo update-alternatives --config java

It is just ignored and when ran again it still has the same jvm selected.

Heres the log:

> alan@AMD64:~$ sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
*     3        /usr/lib/j2sdk1.5-sun/bin/java
      4        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/j2sdk1.5-sun/bin/java' to provide `java'.
alan@AMD64:~$ sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
*     3        /usr/lib/j2sdk1.5-sun/bin/java
      4        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/j2sdk1.5-sun/bin/java' to provide `java'.


Anyone know what could be causing this? Or any way of doing what update-alternatives --config java does manually? I am not afraid of editing files in VI so any kind of fix would be welcomed.

Thanks in advance guys and keep up the good work with this fine fine operating system.

Demon012

---

### Post by Sukarn on 2006-06-03
The starred (*) one is the one that is being used.
So, no. 3 is already being used for java, and you are repeatedly telling it to use number 3.

---

