---
title: "xmame 0.106"
date: 2006-08-10
forum: Gaming &amp; Leisure
---

### Post by sphere02 on 2006-08-10
how can i install xmame 0.106 when i try the debs i got dependices problems

any help?

---

### Post by leech on 2006-08-10
What dependency problems are you having?  I just downloaded (from Debian Sid) the xmame-tools, xmame-common and xmame-sdl and then ran 'sudo dpkg -i xmame-tools_0.106-1_i386.deb xmame-common_0.106-1_all.deb xmame-sdl_0.106-1_i386.deb' and they installed just fine.

Leech

---

### Post by sphere02 on 2006-08-10
ok men what is the url to debian sid? can try

---

### Post by sphere02 on 2006-08-10
mena du härifrån?

[http://ftp.debian.org/debian/pool/non-free/x/xmame/](http://ftp.debian.org/debian/pool/non-free/x/xmame/)

---

### Post by adrianmck on 2006-08-14
Hi all

I tried installing xmame by downloading it from ftp.debian.org/debian/pool/non-free/x/xmame and i had some dependency problems but the main one was with libc6 

dpkg: dependency problems prevent configuration of xmame-tools:
 xmame-tools depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
dpkg: error processing xmame-tools (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xmame-sdl:
 xmame-sdl depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.


I'm trying to install it on Kubuntu.

Also i'm pretty new to linux so i didn't want to mess with this file.

Any help would be very much appreciated.

---

### Post by leech on 2006-08-15
Yeah, you don't want to mess with your libc6 package.

Here's what you'll need to do... which I don't know why they broke this, but ok...

Firstly, you'll need to change your repository.  Just use 'sudo nano /etc/apt/sources.list' and add in somewhere (doesn't matter where, as long as it's a single line) ```
deb-src ftp://ftp.debian.org/debian unstable non-free
``` then run 'sudo apt-get update' from the terminal.  Now you'll have the debian source repository.  You may want to disable this later by editing /etc/apt/sources.list again and just adding a # in front of the line and running 'sudo apt-get update' again.

```
sudo apt-get install build-essential
sudo apt-get build-dep xmame-sdl
sudo apt-get source -b xmame-sdl
```

Wait for a long time (well, depending on how fast your system is.  I remember it took about 45 minutes to compile xmame on a P4 2.26ghz.  Your mileage may vary.)

After this, you should have all the .deb files for xmame and xmess that you will need.  Just do what I said above to install the xmame-sdl, xmame-tools and xmame-common. 

Leech

---

### Post by cor2y on 2006-10-06
Thank you for the info but apparantly
 ```
deb-src ftp://ftp.debian.org/debian unstable non-free
```Now requires a public key to verify that i can't find anywhere anyone knows what it is?

---

