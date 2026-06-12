---
title: "running a .jar"
date: 2005-12-14
forum: General Help
---

### Post by korkow on 2005-12-14
I have java installed and everything, but I can't figure how to run a java file. iv'e tried running it with java, but I get 

Exception in thread "main" java.lang.NoClassDefFoundError: /home/korkow/Desktop/JNetCube/jar

Any help?

---

### Post by TudorB on 2005-12-14
Try using Java Web Start => [http://java.sun.com/products/javawebstart/download.jsp](http://java.sun.com/products/javawebstart/download.jsp)

---

### Post by korkow on 2005-12-14
I *have* tried using javaws, but then then the little java box thing comes up and says "Unable to launch the specified Application". I know this is a valid jar beacuse Iv'e the run it in windows perfectly fine.

---

### Post by bored2k on 2005-12-14
[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix)

Install java. Run the .jar with 
```
java -jar file.jar
```

---

### Post by korkow on 2005-12-14
Now I just get this:

> korkow@linux:~$ java -jar /home/korkow/Desktop/JNetCube.jar
Exception in thread "main" java.lang.UnsupportedClassVersionError: Standalone (Unsupported major.minor version 49.0)
        [INDENT]at java.lang.ClassLoader.defineClass0(Native Method)
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
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)[/INDENT]
korkow@linux:~$ 

---

