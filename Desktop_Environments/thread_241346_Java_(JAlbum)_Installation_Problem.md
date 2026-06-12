---
title: "Java (JAlbum) Installation Problem"
date: 2006-08-22
forum: Desktop Environments
---

### Post by mulata on 2006-08-22
I would like to install the Java Program JAlbum ([http://jalbum.net)](http://jalbum.net)).

When I begin the installation, the following erros occur:

```

sh JAlbuminstall.bin
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.NoClassDefFoundError: ZeroGe
   at java.lang.Class.initializeClass(libgcj.so.7)
   at ZeroGd.<clinit>(DashoA8113)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
   at com.zerog.ia.installer.LifeCycleManager.b(DashoA8113)
   at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
   at com.zerog.ia.installer.Main.main(DashoA8113)
   at java.lang.reflect.Method.invoke(libgcj.so.7)
   at com.zerog.lax.LAX.launch(DashoA8113)
   at com.zerog.lax.LAX.main(DashoA8113)
Caused by: java.lang.ClassNotFoundException: com.apple.mrj.MRJOSType not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/tmp/install.dir.19073/InstallerData/,file:/tmp/install.dir.19073/InstallerData/installer.zip,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   ...9 more
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)




```


I've installed Java on my Ubuntu Linux box:

java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

---

### Post by meng on 2006-08-22
I reckon you may need Sun's Java (as the website states).
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by rejser on 2006-08-22
Not an answer but tip of software. Try albumshaper that's in the repos, quite good, non-java software

---

### Post by andlinux21 on 2006-09-02
I have JAlbum installed on my Dapper Box it's great you need the right Java installed.

---

