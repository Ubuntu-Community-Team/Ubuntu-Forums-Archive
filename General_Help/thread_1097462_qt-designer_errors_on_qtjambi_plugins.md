---
title: "qt-designer errors on qtjambi plugins"
date: 2009-03-16
forum: General Help
---

### Post by strattonbrazil on 2009-03-16
Launching designer throws an error it can't find the correct java virtual machine.

```
JAVA_HOME=/usr/lib/jvm/java-6-sun/jre/
```

```

QtJambi: failed to locate the JVM. Make sure JAVADIR is set, and pointing to your Java installation.
Jambi: failed to initialize...
QtJambi: failed to locate the JVM. Make sure JAVADIR is set, and pointing to your Java installation.
Jambi: failed to initialize...

```

I fix that by setting JAVADIR

```
export JAVADIR=/usr/lib/jvm/java-6-sun/
```

But then I get the following error and don't know where to go from here.  By the way, I'm setting JAVA_HOME and JAVADIR because they're not defined.  I'm using qtjambi-dev packages.  Nothing compiled by me.  Do I need to add something to the classpath?  I just want to be able to save my Qt designer work at .jui files.  

```

QtJambi: Exception pending in native codeException in thread "main" java.lang.NoClassDefFoundError: com/trolltech/tools/designer/CustomWidgetManager
Caused by: java.lang.ClassNotFoundException: com.trolltech.tools.designer.CustomWidgetManager
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Qt Jambi: Cannot load JambiLanguagePlugin due to missing class files

```

---

