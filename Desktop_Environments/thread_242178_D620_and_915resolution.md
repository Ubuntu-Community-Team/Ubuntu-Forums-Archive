---
title: "D620 and 915resolution"
date: 2006-08-23
forum: Desktop Environments
---

### Post by carl.davis on 2006-08-23
I am trying to get my new laptop to utilize the 1440x900 resolution with simply no luck.  I have read several different ways to use the 915resolution and have had no luck with any of them.  Here is what I am doing now:

Setting /etc/defaults/915resolution to 

MODE=5a
XRESO=1440
YRESO=900
BIT=24

After a reboot a 915resolution -l shows that setting in mode 5a.
DefaultDepth 24 in xorg.conf
Subsection Display depth 24 is 1440x900 and no others, except for other depth settings which are all 1440x900.  When I start X it only goes to 1024 x 768 (at least by the screen resolution preferences)  Any help here is greatly appreciated.

---

### Post by Kensey on 2006-08-23
I found this from someone's page at Dartmouth on [getting the D620 working with Dapper]("http://www.math.dartmouth.edu/~sarunas/D620F6.html"):

> Install 915resolution package. Set values in /etc/default/915resolution:

[indent]XRESO=1440
YRESO=900[/indent]

Rerun 915resolution /etc/init.d/915resolution start, then dpkg-reconfigure xserver-xorg selecting 1440x900 video mode. X server restarts in correct mode, direct rendering works (check: glxinfo|grep render).

It looks like you have the first part of that.  You might want to try the dpkg-reconfigure xserver-xorg and see if that fixes it.

---

### Post by carl.davis on 2006-08-23
Thanks, I have several times with no luck.  Could anyone with a working xorg.conf possibly post it?

---

### Post by carl.davis on 2006-08-23
Where does the preferences, screen resolution get its options from.  The options listed in mine are not found anywhere in xorg.conf?

---

