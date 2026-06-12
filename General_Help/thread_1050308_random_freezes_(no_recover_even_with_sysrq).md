---
title: "random freezes (no recover even with sysrq)"
date: 2009-01-25
forum: General Help
---

### Post by mbolo on 2009-01-25
Hi there,
I have Ubuntu Linux 8.04 and, both with 2.6.27-7 and 2.6.27-9 kernels, the system suffers from random freezes. The freeze is very strange: in fact, the X window system is freezed except the mouse, and the system does not respond to termination signals, like: CTRL+ALT+backspace, CTRL+F1...F4 doesn't answer and even ALT+sysrq+B.
The only way to reboot the system is to ssh-login into the system with another machine and then reboot.
/var/log/messages does not contain any useful information.
Hardware: DELL Dimension 9100, Pentium D 3.00 Ghz, 2 GB RAM; 80M in /boot (ext3), 10GB in / (xfs), 512M in swap.
Hardware stress test goes all OK
On this computer is also installed Windows Vista and it does not signals any hardware problems or crash.

Is there something I can do?
Thanks

---

### Post by HermanAB on 2009-01-25
That sounds like a bad video driver to me.  Try changing to the basic VESA driver and see whether it still freezes.  That may give you some idea of what is going wrong.

Cheers,

Herman

---

