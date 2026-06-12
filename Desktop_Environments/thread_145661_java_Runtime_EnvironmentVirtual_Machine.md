---
title: "java Runtime Environment/Virtual Machine"
date: 2006-03-16
forum: Desktop Environments
---

### Post by Manuka on 2006-03-16
Hi all!

I installed SunJVRE 1.5, and it works perfectly as a plugin in Firefox.

But when I try to run java from the Terminal for bioinformatics apps, I have this kind of answer:
```
Exception in thread "main" java.lang.NoClassDefFoundError: while resolving class: cgviz.util.general.L$CGVizFormatter
   at java.lang.VMClassLoader.transformException(java.lang.Class, java.lang.Throwable) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at cgviz.util.general.L.initLogging() (Unknown Source)
   at cgviz.util.general.L.<clinit>() (Unknown Source)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at cgviz.main.CGViz.run(java.lang.String[]) (Unknown Source)
   at cgviz.main.CGViz.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: sun.security.action.GetPropertyAction not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:CGViz-1.0beta1.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   ...9 more
```

I checked for the presence of this libgcj.so.6 file and it's there...

Looking around for help on forums, I saw one that would recommend to choose the right alternative for java, even after Sun JVRE 1.5 was installed.
```
sudo update-alternatives --config java
```

Problem is, I was expecting some choice towards Sun java, but all I got was some Gcj or cgi stuff that seems to cause problems....

Any idea how I could resolve this problem????

Thanks

Manu

---

### Post by Leif on 2006-03-16
The easiest way would probably be to use easyubuntu or automatix to install java for you. search the forums for them.

---

### Post by FIONEX on 2006-03-16
You can't remove the GJC which implements java 1.4.3.  You want the command "java" to run Sun's java 1.5.0.  So basically, that's what the alternatives app does.  It just points the command java in the right direction.  Now if the alternative app can't find your sun java installation, I suggest using Synaptic Package Manager to install java 1.5 again.  I got that error before, and you probably found my thread :P (had the same problem 3 weeks ago).

---

### Post by Manuka on 2006-03-19
Right... thanks for your comments.

I finally found my way out! for some reason, you really need to install sunjava 1.5 from apt-get or synaptic. then you can change your update-alternatives --config java into sunjava....

I found 1.5 update 6 with repositories posted on this wiki page
[https://wiki.ubuntu.com/SeveasPackages](https://wiki.ubuntu.com/SeveasPackages)

cool...

manu

---

