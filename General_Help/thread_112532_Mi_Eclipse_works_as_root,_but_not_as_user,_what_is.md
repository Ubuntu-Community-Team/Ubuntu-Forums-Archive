---
title: "Mi Eclipse works as root, but not as user, what is wrong?"
date: 2006-01-04
forum: General Help
---

### Post by zenitem on 2006-01-04
I've installed eclipse and I have the sun jdk 1.5, wen I run eclipse as root it works perfectly, but when I'm as user it doesn't, can anybody help me please??

:( 

this is my output when I use update-alternatives as user:

[B]enrique@PCDepa:~$ sudo update-alternatives --config java
Password:

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/jvm/java-gcj/bin/java[/B]

I think that there should be the path to the jvm of sun, but when I exectute eclipse as root it appears:

[B]root@PCDepa:/home/enrique# eclipse
using specified vm: /usr/local/jdk1.5.0_06
[/B]

I't is confusing for me.

---

### Post by earobinson on 2006-01-04
i think the problem is because sudo is not running something as root, it runs and allows you to do root things but you are still the current user. (not on ubuntu so i cant check)

try a sudo who to check this out.

if that is the case then it is because your user has 2 paths for java but root only has one

NOTE: this is only a guess

---

