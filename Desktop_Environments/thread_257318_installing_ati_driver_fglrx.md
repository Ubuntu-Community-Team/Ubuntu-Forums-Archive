---
title: "installing ati driver fglrx"
date: 2006-09-14
forum: Desktop Environments
---

### Post by konst88 on 2006-09-14
hello.
a long time ago i had this driver installed, but from some reasons, it stopped working, so i returned to the original xorg.conf.
now, when i follow this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
after reboot, it says it cant find fglrx, and boots into command line instead of to the desktop.
how to make 3d accelerations work?
thx for help.

---

### Post by mitch.c on 2006-09-14
> **konst88 said:**
> hello.
a long time ago i had this driver installed, but from some reasons, it stopped working, so i returned to the original xorg.conf.
now, when i follow this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
Which driver did you install, 8.25.18 (method 1) or 8.28.8 (method 2)?
I just installed 8.25.18 without a hitch.
> **konst88 said:**
> after reboot, it says it cant find fglrx, and boots into command line instead of to the desktop.
What is the output of:
```
find /lib/modules/`uname -r` -iname "*.ko" -or -iname "*.o" | grep fglrx
```
If nothing returns, the module is definitely not there, and you may need to try the installation again and make sure you didn't miss anything.

Have you checked dmesg for anyother hints?

---

### Post by konst88 on 2006-09-15
method 1 also worked before without any problems, but some day, i think cuz of an update, it stopped.
the output of find is:
/lib/modules/2.6.15-26-386/volatile/fglrx.ko
and i tried to install it many times, but it is the same...

---

### Post by mitch.c on 2006-09-15
Are you loading fglrx from /etc/modules?

Why don't you post the output from:
```
lsmod
cat /etc/X11/xorg.conf
```

---

