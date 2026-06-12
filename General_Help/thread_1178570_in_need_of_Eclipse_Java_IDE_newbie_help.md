---
title: "in need of Eclipse Java IDE newbie help"
date: 2009-06-04
forum: General Help
---

### Post by bummm on 2009-06-04
this is my first time ever to try installing & using a Java IDE under linux.

First I installed eclipse from jaunty repository, using symantec. turned out it was 3 years old!
so I uninstalled it. then downloaded the newest version from eclipse's homepage (version 3.4.2).  Followed the installing instructions on their homepage, which means just extracting all the files into a directory on my HD & run it from there. 

I then installed sun-java6-bin , sun-java6-jre, sun-java6-jdk , sun-java6-source.

I created a simple test program in eclipse:

public class bla {
    public static void main(String[] args) {
        system.out.println("bla");}}

then "run as...  -->  java application"

& I get this message in the console:
"Exception in thread "main" java.lang.Error: Unresolved compilation problem: 
 system cannot be resolved at bla.main(bla.java:9)"

what am I missing? or doing wrong?

help appreciated

---

### Post by McNils on 2009-06-04
System.out.println("bla");

---

### Post by bummm on 2009-06-04
thanks, but not sure how that helps me

---

### Post by bummm on 2009-06-04
oh i see, capitol letter...... thanks. haha, I suck, thought it was something else but a compiling error on my one line of code

---

### Post by smartidiot on 2009-06-05
Yeah, just need to remember that java is case sensitive :)

---

