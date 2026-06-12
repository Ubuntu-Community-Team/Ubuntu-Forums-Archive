---
title: "Using compiz-extra and compiz-settings"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by rstuart on 2007-04-25
Hi all,

I have managed to get the Desktop Effects in fiesty working once i installed the gnome-compiz-manager. I also came across the compiz-extra package so i installed it. I have no idea how to use it however. I see there is a program compiz-settings listed on the compiz.org site which should let me configure and use compiz-extra but no matched found using aptitude. 

Am i not looking hard enough or do i have to install this outside of apt? If so, can someone point me to a list of instructions to follow for doing this

Thanks

---

### Post by thegreenman on 2007-04-27
same deal here, where are the settings?

---

### Post by anandi on 2007-04-28
Need to know how to go about doing the settings myself ...

Any help would be appreciated.

---

### Post by maher_79 on 2007-06-11
I was reading around and i think we need compiz-extra-plugins to be able to use the compiz-extra.    but when i tried to do that i got the below error:

```
maher@maher-ubuntu:~$ sudo apt-get install compiz-extra-plugins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  compiz-extra-plugins
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/310kB of archives.
After unpacking 1565kB of additional disk space will be used.
(Reading database ... 112738 files and directories currently installed.)
Unpacking compiz-extra-plugins (from .../compiz-extra-plugins_0.5.0.2-1~3v1ubuntu0_i386.deb) ...
[COLOR="Red"]dpkg: error processing /var/cache/apt/archives/compiz-extra-plugins_0.5.0.2-1~3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/lib3d.so', which is also in package compiz-extra
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:[/COLOR]
 /var/cache/apt/archives/compiz-extra-plugins_0.5.0.2-1~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please help me out here - New to Ubuntu and don't know what i'm doing wrong! :sad:

---

### Post by MatrixGIO on 2007-06-14
same deal here - i get the same error when trying to install compiz-extra

Unpacking compiz-extra (from .../compiz-extra_0.3.6.1-0ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-extra_0.3.6.1-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/lib3d.so', which is also in package compiz-extra-plugins
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-extra_0.3.6.1-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

any clue how to overcome it ?

---

### Post by maher_79 on 2007-06-14
To manage compiz extra we need gnome-compiz-manager-extra BUT i'm getting errors trying to install that.

I've already started a thread about that over here [http://ubuntuforums.org/showthread.php?t=471682](http://ubuntuforums.org/showthread.php?t=471682)

Please go there and add the problem you are having.  I hope someone will be able to help!

---

