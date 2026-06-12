---
title: "No Gnome With SSD After Restart"
date: 2011-04-01
forum: Desktop Environments
---

### Post by ZoZat on 2011-04-01
I'm doing a fresh install of Ubuntu 10.10 on a new SSD.  All seems to go well, did all the updates.  Computer rebooted numerous times without a hitch.  Here's the problem...soon as I turn the computer off and restart it, I can no longer get to the desktop.
I'm presented with a prompt.  I can login but startx and gdm wasn't the ticket.  Could it be grub cause the trouble?

I'm new at linux.  Could I please get some help.

---

### Post by Copper Bezel on 2011-04-01
What output did you get when you tried startx?

---

### Post by ZoZat on 2011-04-01
I've reinstalled the OS several times with the same result.

This is what I get when I enter startx:

X.Org. X Server 1.9.0
Release Date: 2010-08-20
X Protocol 11, Revision 0
Build Operating System:  Linux 2.6.24-8-server  i686 Ubuntu
Current Operating System:  Linux Laptop-NV58-Series 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-2.6.35-generic  root=UUID-e7b5c828-d5bc-4e02-acd6-eb2c996f63df  ro splash vga-799 quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
Build Date:  09 January 201112:14:58PM
xorg-server 2:1.9.0-0ubuntu7.3
Current version of pixman:  0.18.4
(==) Log file: "/var/log/Xorg.0.log". Time: Friday Apr 1 11:09:30 2011
(==) Using system config directory "/var/share/X11/xorg.conf.d"
(EE) intel (0): No kernel modesetting driver detected
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found

xinit:  No such file or directory (errno2):  unable to connect to X server
xinit:  No such process (errno3):  Server error

---

