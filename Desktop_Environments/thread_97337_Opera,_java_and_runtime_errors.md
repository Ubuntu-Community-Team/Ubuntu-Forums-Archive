---
title: "Opera, java and runtime errors"
date: 2005-11-30
forum: Desktop Environments
---

### Post by forlog on 2005-11-30
Hi,

I have installed Opera 8.51 and jdk-1_5_0_05-linux-i586.rpm. Then I set path to java to /usr/java/jdk1.5.0_05/jre/lib/i386 in the preferences. When I try to open any website with java applet Opera prints such message

motifwrapper: X Error: BadWindow (invalid Window parameter)
motifwrapper: X Error: serial=0x31e, request=0x2, request_minor=0x0, resource=0x2a0001b
motifwrapper: X Error: BadWindow (invalid Window parameter)
motifwrapper: X Error: serial=0x325, request=0x4, request_minor=0x0, resource=0x2a0001b
motifwrapper: X Error: BadWindow (invalid Window parameter)
motifwrapper: X Error: serial=0x32a, request=0x4, request_minor=0x0, resource=0x2a0001a
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object

and quits.

Any ideas what's wrong?

---

### Post by Kray on 2005-12-01
Try this - type

```
sudo update-alternatives --config java
```

and choose proper java location. Example output:

```
There are 3 alternatives which provide `java'.

Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/lib/j2sdk1.5-sun/bin/java
```

First 2 positions are installed out-of-box on Breezy. Third one is JDK downloaded from [http://ubuntu.tower-net.de/ubuntu/dists/breezy/java/binary-i386/](http://ubuntu.tower-net.de/ubuntu/dists/breezy/java/binary-i386/). If ure not Java developer u can download just JRE. Of course u can try first with your current Java installed from RPM (via alien I suppose?).

[http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) is good source for Java prepackaged in DEB format. More handy than RPM format and u can add it to repositories, too.

Hope this helps :-)

---

### Post by akiro.yamamoto on 2005-12-01
Also direct Opera to the plugins installed for firefox.
That should help..
[https://wiki.ubuntu.com/RestrictedFormats#head-ef347c277a133b64af0600bd1bf24bc64e7038b8](https://wiki.ubuntu.com/RestrictedFormats#head-ef347c277a133b64af0600bd1bf24bc64e7038b8)
Regards
If you need more info check the links in my sig
:smile:

---

### Post by Kray on 2005-12-01
And if ya have any problems with Opera and plugins run:

```
opera -debugplugin
```

It will show ya what plugins are loaded, from what paths and which are broken.

Cheers

---

### Post by forlog on 2005-12-01
```
sudo update-alternatives --config java
```
gives me:
```

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/jvm/java-gcj/bin/java

Press enter to keep the default[*], or type selection number:

```

There is no sun java on the list. Does it mean that java was not installed properly?

******************    edit   ************************

I've installed  jdk-1_5_0_05-linux-i586.bin instead of  jdk-1_5_0_05-linux-i586.rpm and now everything works ok :D
Thanks.

---

