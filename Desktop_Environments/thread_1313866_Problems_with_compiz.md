---
title: "Problems with compiz"
date: 2009-11-04
forum: Desktop Environments
---

### Post by fernandoch on 2009-11-04
Hello,

When starting compiz in Ubuntu 9.10 with 

```
compiz --replace
``` 

I get this error

```
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity
```

With Ubuntu 9.04, I had compiz working properly.

Any clues?

---

### Post by kellemes on 2009-11-04
Is your system up to date?

It seems you're not the only with this problem..
[https://bugs.launchpad.net/ubuntu/+source/parti-all/+bug/442256]("https://bugs.launchpad.net/ubuntu/+source/parti-all/+bug/442256")
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/442197]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/442197")
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441577]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441577")

---

### Post by fernandoch on 2009-11-04
Yes it is up to date :(

I found these bugs too, but with no clear solution.

Some say to modify the Xorg.conf file which does not exist on my system. I should create, but I would like to try in here to see if someone has a better solution...

---

### Post by fernandoch on 2009-11-06
Well it seems I am not the only one having problems with ATI Radeon. They are even comparing Karmic to Vista! Imagine...

Maybe I should get back to 9.04 Jaunty.

Check this

[http://www.omgubuntu.co.uk/2009/11/karmic-ubuntus-vista.html](http://www.omgubuntu.co.uk/2009/11/karmic-ubuntus-vista.html)

---

### Post by schilcha on 2009-11-06
I too had problems to get compiz up and running for my Radeon 9600 after upgrading to karmic. Software rasterizer was active as well.

I found another thread in the forums pointing to an faq page at freedesktop.org ([http://dri.freedesktop.org/wiki/DriTroubleshooting](http://dri.freedesktop.org/wiki/DriTroubleshooting)), which gives an extensive set of potential problems and the appropriate solutions.

Here is what was my problem:
The agp-module (agpart) wasn't loaded prior to the radeon kernel module. Creating a file (I called it ati.conf) in /etc/modprobe.d with the following contents
```

install  radeon /sbin/modprobe agpgart; /sbin/modprobe --ignore-install radeon

```
did the trick for me.

Hope this helps!

---

### Post by fernandoch on 2009-11-07
I just had to activate the FGLRX restricted drivers and it worked.

---

