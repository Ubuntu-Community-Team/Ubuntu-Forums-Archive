---
title: "xterm via cygwin (xwin.exe) not working"
date: 2007-02-15
forum: Desktop Environments
---

### Post by twofruits on 2007-02-15
Hi All

I've started xwin.exe from cygwin on my win-xp box, and then started an ssh session into my ubuntu (6.10) server using putty.

I then export my display, and attempt to start xterm.

cygwin reports the following message :-

Xlib: connection to "10.29.36.73:0.0" refused by server
Xlib: No protocol specified

xterm Xt error: Can't open display: 10.29.36.73:0.0

and in the xwin log I get the following :-

AUDIT: Fri Feb 16 12:16:47 2007: 2960 xwin: client 1 rejected from IP 10.29.36.1
54

What is very very strange is that if I kill xwin on the xp box, then start humminbird exceed, and do the same thing, it works perfectly.

Any idea what I'm doing wrong with xwin/cygwin ?

Thanks

---

