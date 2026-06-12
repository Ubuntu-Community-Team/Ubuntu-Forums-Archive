---
title: "installing sun java 6 jre"
date: 2008-12-27
forum: General Help
---

### Post by threedguy on 2008-12-27
I'm having a lot of trouble installing the sun version of java.  I've installed sun-java6-fonts, sun-java6-jre, and sun-java6-plugin using synaptic, but when I run java -version in the terminal I get this:

$ java -version
Error: could not open `/usr/lib/jvm/java-6-sun/jre/lib/i386/jvm.cfg'

I browsed to the file and it's showing a broken link to an old, uninstalled version of OpenJDK.

I have tried running $ sudo update-java-alternatives -s java-6-sun
to no avail.  If anyone has any idea how to fix this I would appreciate it.

---

### Post by taurus on 2008-12-27
Run these commands again and see what happens.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
Remember, you need to accept the licensing first before it is actually installed so press the Tab key to highlight the <OK> and Return to accept it.

---

### Post by threedguy on 2008-12-28
Just tried that, and I'm still getting the same response from java -version.  Here is what it said after the second line:

$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-bin set to manually installed.
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
sun-java6-plugin is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic fakeroot debhelper intltool-debian
  po-debconf libseda-java gettext libgcj-common classpath-gtkpeer tzdata-java
  lesstif2 libtimedate-perl dpkg-dev classpath-common html2text patch
  classpath libswt3.2-gtk-jni linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

---

