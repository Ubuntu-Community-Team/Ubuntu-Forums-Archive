---
title: "Compiz Disables Flash Clicking"
date: 2010-02-17
forum: Desktop Environments
---

### Post by zjagannatha on 2010-02-17
I've had this issue with Flash for a while where I can't click on anything. After I upgraded a friend's linux box and installed Compiz she started having the same issue and suggested I disable desktop effects.
After I disabled desktop effects sure enough, flash started working again.

I'm not exactly sure what's causing the problem. I'll try disabling specific options when I get time later and post anything I find. In the meantime anyone else have this issue?

Corresponding topic on Compiz Forums:
[http://forum.compiz.org/viewtopic.php?f=86&t=12338](http://forum.compiz.org/viewtopic.php?f=86&t=12338)

---

### Post by Addicted247 on 2010-02-17
You might be experiencing this bug:

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

I had the same problem and solved it by downloading the flash plugin (x64) and putting it into the firefox plugin directory (the following link is for the x64 bit version of the plugin):

```
$ wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
$ tar xf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
$ sudo cp libflashplayer.so /usr/lib/firefox-addons/plugins/

```

---

### Post by soulsource on 2010-07-08
You can also edit the nspluginwrapper config file:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

And add 
export GDK_NATIVE_WINDOWS=1
before the last line.

My file contains the following:
> 
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer


---

