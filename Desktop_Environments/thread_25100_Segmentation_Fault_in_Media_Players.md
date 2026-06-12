---
title: "Segmentation Fault in Media Players"
date: 2005-04-09
forum: Desktop Environments
---

### Post by Grimmy on 2005-04-09
I updated my Warty install to Hoary and now I can't run my favourite media players

XMMS, VLC and Amarok all won't start - if started from a terminal then they all display the message "segmentation fault"

Any ideas, or suggestions on how to get further information to help diagnose this problem?

---

### Post by p!=f on 2005-04-09
Is your box really completely upgraded to Hoary?
```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install

```
Don't you have some broken packages installed?
```

dpkg -l | grep -v ^ii

```
Can you strace any of that players?
```

strace xmms

```
At the very end (last 10,30 lines, near the segmentation fault error) you should see what is that segfaulting on.

---

### Post by Grimmy on 2005-04-09
[QUOTE=p!=f]Is your box really completely upgraded to Hoary?
```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install

```
[/quote]

Yes, thats all done.

[QUOTE=p!=f]
Don't you have some broken packages installed?
```

dpkg -l | grep -v ^ii

```

[/quote]

I'm not sure what the output of this means... but here it is:

```

||/ Name           Version        Description
+++-==============-==============-============================================
rc  fam            2.7.0-5ubuntu2 File Alteration Monitor
rc  gnome-cpufreq- 0.1.3-1        CPU Frequency Scaling Monitor applet for GNO
rc  libapache2-mod 4.3.10-10ubunt server-side, HTML-embedded scripting languag
rc  libfam0c102    2.7.0-5ubuntu2 client library to control the FAM daemon
rc  libgtop2-4     2.8.0-0ubuntu1 Libraries for gtop system monitoring library
rc  libnautilus2-2 2.8.1-0ubuntu1 libraries for nautilus components - runtime
rc  libopenh323-1. 1.13.4-3       H.323 aka VoIP library
rc  libpt-1.6.3    1.6.5-3ubuntu1 Portable Windows Library
rc  netkit-inetd   0.10-9ubuntu3  The Internet Superserver
rc  php4-mysql     4.3.10-10ubunt MySQL module for php4
rc  phpbb2         2.0.8a-3       A fully featured and skinneable flat (non-th
rc  phpbb2-conf-my 2.0.8a-3       Automatic configurator for phpbb2 on MySQL d
rc  phpmyadmin     2.6.1-rc1-1    A set of PHP-scripts to administrate MySQL o
rc  proftpd        1.2.9-12       Versatile, virtual-hosting FTP daemon
rc  proftpd-common 1.2.9-12       Versatile, virtual-hosting FTP daemon
rc  pure-ftpd      1.0.17a-1      Pure-FTPd FTP server
rc  pure-ftpd-comm 1.0.17a-1      Pure-FTPd FTP server (Common Files)
rc  rmail          8.13.2-1       UUCP remote mail handler
rc  sendmail-bin   8.13.2-1       A powerful, efficient, and scalable Mail Tra
rc  trashapplet    0.4-0ubuntu1   Trash applet for GNOME.
rc  xserver-xfree8 4.3.0.dfsg.1-6 the XFree86 X server

```

[QUOTE=p!=f]
Can you strace any of that players?
```

strace xmms

```
At the very end (last 10,30 lines, near the segmentation fault error) you should see what is that segfaulting on.[/QUOTE]

Again, not too sure about this

```

access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libnvidia-tls.so.1", O_RDONLY) = 9
read(9, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \3\0\000"..., 512) = 512
lseek(9, 1272, SEEK_SET)                = 1272
read(9, "\4\0\0\0\20\0\0\0\1\0\0\0GNU\0\0\0\0\0\2\0\0\0\2\0\0\0"..., 32) = 32
fstat64(9, {st_mode=S_IFREG|0644, st_size=2076, ...}) = 0
old_mmap(NULL, 5556, PROT_READ|PROT_EXEC, MAP_PRIVATE, 9, 0) = 0xb6787000
old_mmap(0xb6788000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 9, 0) = 0xb6788000
close(9)                                = 0
mprotect(0xb6787000, 4096, PROT_READ|PROT_WRITE) = 0
mprotect(0xb6787000, 4096, PROT_READ|PROT_EXEC) = 0
mprotect(0xb6789000, 7475200, PROT_READ|PROT_WRITE) = 0
mprotect(0xb6789000, 7475200, PROT_READ|PROT_EXEC) = 0
mprotect(0xb6eda000, 393216, PROT_READ|PROT_WRITE) = 0
mprotect(0xb6eda000, 393216, PROT_READ|PROT_EXEC) = 0
munmap(0xb6f52000, 68583)               = 0
open("/dev/zero", O_RDWR)               = 9
mmap2(NULL, 8192, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE, 9, 0) = 0xb6f61000
close(9)                                = 0
getpid()                                = 11542
mmap2(NULL, 622592, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb66ef000
getpid()                                = 11542
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++

```

---

### Post by p!=f on 2005-04-09
rc means a package is removed but configuration files were left so nothing bad :)

Try to temporarily change the driver in /etc/X11/xorg.conf from nvidia to nv to see any difference...

---

### Post by Grimmy on 2005-04-12
I managed to fix the problem by installing an older version of the nvidia drivers (66.29).   Thanks for your help.

---

### Post by Stefan Koopmanschap on 2005-06-04
[QUOTE=Grimmy]I managed to fix the problem by installing an older version of the nvidia drivers (66.29).   Thanks for your help.[/QUOTE]

where did you get these older nvidia drivers from? did you install those using apt-get/synaptic?

---

### Post by Grimmy on 2005-06-06
[QUOTE=Stefan Koopmanschap]where did you get these older nvidia drivers from? did you install those using apt-get/synaptic?[/QUOTE]

I got them from here...

[http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html)

---

### Post by Stefan Koopmanschap on 2005-06-06
[QUOTE=Grimmy]I got them from here...

[http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html)[/QUOTE]

thanks, I'll try it :)

---

### Post by DiemonasLt on 2005-06-12
i have the same problem. It seems that this problem is coused by nvidia-glx driver. So i installed mesa3 driver and xmms is working without problems :).
Sorry for my english

---

