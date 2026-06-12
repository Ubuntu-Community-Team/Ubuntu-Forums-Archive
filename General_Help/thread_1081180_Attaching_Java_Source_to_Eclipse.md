---
title: "Attaching Java Source to Eclipse"
date: 2009-02-26
forum: General Help
---

### Post by sasanpad on 2009-02-26
Hi All,

I need to attach Java's source to Eclipse so I can hold Ctrl down and click on Java's methods and get the source code. I have followed [http://ubuntuforums.org/showthread.php?t=499365](http://ubuntuforums.org/showthread.php?t=499365) but it did not work.

It says it cannot find the source while it is attached to rt.jar.

If you know its done please let me know. (I use Eclipse 64 bit)

Thanks in advance.
Sassan

---

### Post by sasanpad on 2009-02-26
I solved it myself. I downloaded Sun source code in synaptic and then added the src.zip file to rt.jar "Attach Source" in preferences->installed JRE.

---

### Post by sam1948 on 2010-11-16
was solved a long time ago but i found a good practice.

in a terminal run this:
```
sudo apt-get install sun-java6-source
```
(or download manually [http://download.java.net/jdk6/source/]("http://download.java.net/jdk6/source/"))

open eclipse and write a main function with the following line:
```
Object o = new Object();
```
place the mouse on the second Object word.
press Ctrl + <mouse right click>
when u will see "attach source"
browse to the location of source
-the jar file u downloaded or 
"/usr/lib/jvm/java-6-sun-1.6.0.22" src.zip file for the apt way.

eclipse will think 4 1 sec and u will see the source

enjoy

---

