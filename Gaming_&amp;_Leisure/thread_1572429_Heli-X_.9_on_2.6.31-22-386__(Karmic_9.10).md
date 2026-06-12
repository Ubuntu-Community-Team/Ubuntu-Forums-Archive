---
title: "Heli-X .9 on 2.6.31-22-386  (Karmic 9.10)"
date: 2010-09-11
forum: Gaming &amp; Leisure
---

### Post by vector on 2010-09-11
hi all just tried installing heli-x and it returned this

any ideas?
cheers

sorry should add I have JRE ver 6 I think according to synaptic
but java -version returns this

installedjava -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

yep i know not what i doin :)

```
./runHELI-X.sh 
Exception in thread "main" java.lang.UnsupportedClassVersionError: Bad version number in .class file
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(Unknown Source)
    at java.security.SecureClassLoader.defineClass(Unknown Source)
    at java.net.URLClassLoader.defineClass(Unknown Source)
    at java.net.URLClassLoader.access$100(Unknown Source)
    at java.net.URLClassLoader$1.run(Unknown Source)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(Unknown Source)
    at java.lang.ClassLoader.loadClass(Unknown Source)
    at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
    at java.lang.ClassLoader.loadClass(Unknown Source)
    at java.lang.ClassLoader.loadClassInternal(Unknown Source)

```

wrong version of Java loaded and couldnt work out how to switch it

---

