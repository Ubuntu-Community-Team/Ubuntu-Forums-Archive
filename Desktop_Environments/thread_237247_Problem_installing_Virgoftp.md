---
title: "Problem installing Virgoftp"
date: 2006-08-15
forum: Desktop Environments
---

### Post by Enigmatic on 2006-08-15
I try running ./virgoftp to install, but I get this error:


```
Exception in thread "main" java.lang.UnsupportedClassVersionError: edu/sysu/virgoftp/gui/VirgoFTP (Unsupported major.minor version 49.0)
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

Something to do with Java...here is my Java version

java version "1.5.0_06"```

Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Server VM (build 1.5.0_06-b05, mixed mode)
```


Ideas?

---

