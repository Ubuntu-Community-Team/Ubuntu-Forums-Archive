---
title: "HELP! What does this java error mean??"
date: 2011-08-19
forum: Gaming &amp; Leisure
---

### Post by RawrFace on 2011-08-19
Hey Im trying to run an RSPS via commands:

piers@piers-Inspiron-1525:~$ cd Desktop/controlledpkz

piers@piers-Inspiron-1525:~$ java runescape.jar

But everytime i does so (this has worked on many servers before) I get this error:

Exception in thread "main" java.lang.NoClassDefFoundError: runescape/jar
Caused by: java.lang.ClassNotFoundException: runescape.jar
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: runescape.jar. Program will exit.


NEED HELP FAST!

Thankyou ever so much!

---

### Post by RawrFace on 2011-08-20
BUMP Anyone?

---

### Post by kvarley on 2011-08-20
You aren't launching it properly.

I seem to remember with runescape stuff you have to specify the class path manually.

Do *java --help* and read the *-cp* option.

---

### Post by Nytram on 2011-08-20
Jar files are launched like this:

**java -jar runescape.jar**

---

### Post by doorknob60 on 2011-08-20
> **Nytram said:**
> Jar files are launched like this:

**java -jar runescape.jar**
This.

Also, hate to break it to you, but it seems like most RSPSes out there nowadays are extremely unstable on Linux for whatever reason (not sure why). If you get random crashes and bad bugs with the game's UI, your only option might be to run the Windows version of Java in Wine. Hopefully you don't have to, but you might, I know my friend used to play on a lot of RSPSes, and most of them he had to use Wine.

---

