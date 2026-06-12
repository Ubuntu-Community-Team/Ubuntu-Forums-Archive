---
title: "XGL gdm.conf issue..."
date: 2006-10-30
forum: Desktop Environments
---

### Post by resistdesign on 2006-10-30
I tried to run XGL by default and edited /etc/X11/gdm/gdm.conf

I put:
0=Xgl
and commented out standard:
#0=Standard

It wouldn't load my gui so in terminal mode I used vim to undo that and put:
#0=Xgl
and:
0=Standard

But it's acting like I didn't do that and is still trying to load xgl.

Also, the tutorial I followed to run xgl told me to make a "~/.Xsession" file which I did and couldn't seem to get ubuntu to use it.

I know XGL works because accidentally executed "~/.Xsession" while in xserver and got some sort of a stacked double desktop of xgl in xserver with two task bars on top of each other.

But I can't seem to get xgl to run as my main gui.

Any help would be awesome!!!:mrgreen:

---

### Post by resistdesign on 2006-10-30
Does anybody know what to do?

---

### Post by resistdesign on 2006-10-30
Oh come on, am I really that ugly??

---

