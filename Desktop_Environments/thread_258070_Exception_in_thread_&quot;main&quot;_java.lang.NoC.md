---
title: "Exception in thread &quot;main&quot; java.lang.NoClassDefFoundError: input.java"
date: 2006-09-15
forum: Desktop Environments
---

### Post by alien^ on 2006-09-15
alien@alien-desktop:~/java/java1st$ java input.java
Exception in thread "main" java.lang.NoClassDefFoundError: input.java
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: input.java not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)

what does this mean?

---

### Post by parktownprawn on 2006-09-15
Have you installed java?

It looks like your machine is trying to use gnu version of java which might not work too well.

see

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by alien^ on 2006-09-15
[[IMG]http://img227.imageshack.us/img227/41/snapshot8ue4.th.jpg[/IMG]](http://img227.imageshack.us/my.php?image=snapshot8ue4.jpg) what i have installed...

id did this:
update-java-alternatives -l
sudo update-java-alternatives -s java-1.5.0-sun
and now i get:
alien@alien-desktop:~/java/java1st$ java input.java
Exception in thread "main" java.lang.NoClassDefFoundError: input/java

---

### Post by parktownprawn on 2006-09-15
hmmm - sorry not sure what the problem is

---

### Post by alien^ on 2006-09-15
my mistake java for binary files and for compiling is javac :)

---

