---
title: "Brutal File Manager won't install!"
date: 2010-05-18
forum: Gaming &amp; Leisure
---

### Post by Mountain Dew Overdose on 2010-05-18
This evening I was bored and googling random games for Linux, and so eventually I happened upon [Brutal File Manager]("http://www.forchheimer.se/bfm/"). It's basically a first person shooter and a file manager...Downloads folder cluttered? Walk into it and shoot all the files with any weapon of choice :P Anyways though, I followed the instructions to install it...but whenever I try to run it I just get...

```
tyler@lintmagnet:~/Downloads/bfm-1.2$ bfm
Exception in thread "main" java.lang.NoClassDefFoundError: javax/media/j3d/Node
Caused by: java.lang.ClassNotFoundException: javax.media.j3d.Node
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
Could not find the main class: Bfm. Program will exit.
tyler@lintmagnet:~/Downloads/bfm-1.2$
```I've installed Java JDK and Java3D from synaptic...but it still gives me that output when I try to run it, someone help :(

Also the thread name is incorrect to the issue I'm having...I was tired when I wrote this and forgot, if any mod or someone could change Install to Run, it'd be appreciated!

---

