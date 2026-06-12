---
title: "dpkg error"
date: 2006-06-01
forum: Desktop Environments
---

### Post by majkmil on 2006-06-01
I get this error when trying to installl the debs with the proprietary drivers from ATI.

mark@ubuntu:~/ati$ sudo dpkg -i xorg-driver-fglrx_8.25.18-1_i386.deb
(Reading database ... 135622 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 8.24.8-1 (using xorg-driver-fglrx_8.25.18-1_i386.deb) ...
Removing `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx'
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1.2' with
different file `/usr/share/fglrx/diversions/libGL.so.1.2', not allowed
dpkg: error processing xorg-driver-fglrx_8.25.18-1_i386.deb (--install):
subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
xorg-driver-fglrx_8.25.18-1_i386.deb

Can anyone help with this please.

---

### Post by majkmil on 2006-06-01
can't get no love?

---

### Post by majkmil on 2006-06-01
Gee Thanks

---

### Post by pertti on 2006-06-04
Try this: [http://www.ubuntuforums.org/showthread.php?t=186602]("http://www.ubuntuforums.org/showthread.php?t=186602")

I have a similar problem, though not exactly the same. When I "apt-get remove xorg-driver-fglrx" I get the following error:

```
dpkg-divert: mismatch on divert-towhen removing `diversion of usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx'
found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
```

I tried moving around those files, but still no luck. It seems that that's a problem with the dpkg database, since there are two divertions of the same file, not an overwriting a file problem. So far the threads I've seen about this problem have got no solution. Any idea?

---

### Post by pertti on 2006-06-04
Ok, I've found [a solution]("http://ubuntuforums.org/showthread.php?t=143283&page=12") from Cavalierski for my problem. It's the last post on that page.

```
sudo rm /var/lib/dpkg/info/xorg-driver-fglrx.postrm
sudo dpkg --purge xorg-driver-fglrx
sudo aptitude update
sudo aptitude install xorg-driver-fglrx
```

---

