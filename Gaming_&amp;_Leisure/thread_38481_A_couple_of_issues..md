---
title: "A couple of issues."
date: 2005-05-31
forum: Gaming &amp; Leisure
---

### Post by trezy on 2005-05-31
First no GLX stuff works for me.  I have a Nvidia TNT2 32mb video card.  I have the Ubuntu drivers and i'm running on Kubuntu-desktop cause I messed up Gnome.

Also I recentlly got SimCity 3000 Unlimited and it won't work at all.  It starts to load in the taskbar then the task thing goes away and nothing happens.

Can someone help me with this cause I really want to play games!

---

### Post by thrift on 2005-05-31
attach your /etc/X11/xorg.conf

if you have a /proc/driver/nvidia/agp/status:
cat /proc/driver/nvidia/agp/status

and post the output of that command

run glxgears in a terminal window and post the output of that.

from a terminal run:
dmesg > dmesg.txt

and attach dmesg.txt from your home directory.

With this stuff we should be able to help you much easier.

---

### Post by ltmon on 2005-05-31
I tried SimCity 3000 Unlimited a while back, and never got it working.  In fact I couldn't even find someone who had it working at the time.  I guess some kind of upgrade broke it big time, and Loki weren't around to fix it by that stage.

---

