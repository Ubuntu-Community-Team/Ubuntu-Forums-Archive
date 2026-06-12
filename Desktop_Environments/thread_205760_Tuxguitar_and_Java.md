---
title: "Tuxguitar and Java"
date: 2006-06-28
forum: Desktop Environments
---

### Post by NinjitsuStylee on 2006-06-28
Hi all.  So I was looking around gnomefiles.org and I saw this program called [TuxGuitar]("http://www.gnomefiles.org/app.php?soft_id=1248"), so I decided to have a go at it.  

Upon realizing that I needed "sunj2sdk1.5" (it was a dependency) and that it wasn't showing up like that in Synaptic, I decided to do some searching, and came across this tutorial:

[http://www.minds.nuim.ie/~voyager/blog/index.php?/archives/24-The-CORRECT-way-to-install-Sun-Java-on-DebianUbuntu.html](http://www.minds.nuim.ie/~voyager/blog/index.php?/archives/24-The-CORRECT-way-to-install-Sun-Java-on-DebianUbuntu.html)

So I followed the tutorial (I downloaded jdk-1_5_0_07-linux-i586.bin and turned it into a .deb as per the above link).

The TuxGuitar deb tells me that all dependencies are satisfied.  However when I try to run "tuxguitar" from the terminal, I'm getting the following error:

```
Exception in thread "main" java.lang.UnsupportedClassVersionError: org/herac/tuxguitar/gui/TuxGuitar (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)

```

Does anybody have any idea what's going on?  Did I not install the right java SDK?  Sigh, why can't they just have the right version on synaptic :(

---

### Post by NinjitsuStylee on 2006-07-04
bump

---

### Post by www.rzr.online.fr on 2006-10-26
Hi,

I am responsible for the debian package of tuxguitar, any ubuntu developper want to cooperate on it ? 
@ [http://rzr.online.fr/q/tuxguitar](http://rzr.online.fr/q/tuxguitar)

Updated

---

### Post by the_priest on 2006-10-30
Man this app sounds great.
I'm a guitarist in a band, who is busy testing out Ubuntu Dapper in hopes of maybe migrating completely (except for a small XP partition for those games i can't emu) and this program will be a great help to me instead of GuitarPro 5, which is what i used to use.

PLEASE someone who knows what they doing help out to develop this for ubuntu! :)

---

