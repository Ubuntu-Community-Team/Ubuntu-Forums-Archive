---
title: "X server for display :0 terminated unexpectedly"
date: 2008-11-12
forum: Desktop Environments
---

### Post by dunnerz on 2008-11-12
Hi,

Just upgraded to Intrepid and having a bit of a problem.

Usually when I try to resize something on the deskop, but also randomly, X crashes/restarts and I get chucked back to the login screen.

I get this message in /var/log/syslog

kdm[5021]: X server for display :0 terminated unexpectedly

Can't find anything on Google about it (that's relevant) - any one have any ideas (few finished this post before it restarted, excellent!)

Thanks.

---

### Post by dunnerz on 2008-11-12
Futher to that
/var/log/kdm

```

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xffffe420]                               
2: [0xffffe420]                               
3: /usr/bin/X(ProcSetClipRectangles+0xc1) [0x808acb1]
4: /usr/bin/X(Dispatch+0x34f) [0x808c89f]            
5: /usr/bin/X(main+0x47d) [0x8071d1d]                
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b4d685]
7: /usr/bin/X [0x8071101]                                           
Saw signal 11.  Server aborting.  


```

---

### Post by Vladimir23 on 2008-11-19
I have exactly the same problem. 


Backtrace:
0: /usr/bin/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xffffe420]
2: [0xffffe420]
3: /usr/bin/X(ProcSetClipRectangles+0xc1) [0x808acb1]
4: /usr/bin/X(Dispatch+0x34f) [0x808c89f]
5: /usr/bin/X(main+0x47d) [0x8071d1d]
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b39685]
7: /usr/bin/X [0x8071101]
Saw signal 11.  Server aborting.

Have not found any solution. Xorg crashes even if i switch my laptop from intel to NVIDIA video card.

---

### Post by dunnerz on 2008-11-19
It also affects gnome desktop - so it is not just Kubuntu related.

You might want to take a look at this bug report - I think it might be similar?
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/273505](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/273505)

I just can't work out what it is, I've tried deleting xorg.conf, re-running dpkg-reconfigure xserver-xorg (or which ever way that round that command is) - just no idea.

Although I have a theory that it is related the the graphics driver and latest kernel version :(

---

### Post by Vladimir23 on 2008-11-19
It has no relation to the latest kernel version. I have the old one. Moreover I do not use kde or gnome, but xmonad. The crash appears when I work in firefox or scribus. With Xorg 7.3 I have not experienced such problem.

---

### Post by dunnerz on 2008-11-19
So sounds like it is related to the latest version of XORG.

I wonder if it is possible to roll back 8.10 to an earlier version of XORG?

I might try a fresh install, see if that makes a difference, but that is something that you should not have to do.

Cheers.

---

### Post by Vladimir23 on 2008-11-19
I have made an attempt to roll back to 7.3... but... keyboard start acting very weird... arrows do not work at all. However I have downgraded all the packeges and libs related to x11 or xorg including xkb-data.

---

### Post by dunnerz on 2008-11-20
I gave up - went back to hardy :(

---

