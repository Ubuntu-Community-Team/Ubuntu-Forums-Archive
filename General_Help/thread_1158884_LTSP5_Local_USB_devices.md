---
title: "LTSP5 Local USB devices"
date: 2009-05-14
forum: General Help
---

### Post by keenboy on 2009-05-14
Hello,

I am trying to get a digital camera to work with my LTSP thin clients. I have followed the tutorial here:

[https://wiki.ubuntu.com/EnableLTSP5LocalDevices](https://wiki.ubuntu.com/EnableLTSP5LocalDevices)

But it will not work. The camera is recognised by the thin client when I run dmesg as root on a Vterminal (alt-F1 at login). If I run dmesg as a user it's not recognised.

To get local devices to work each user needs to be a member of the fuse group. I have done this and /etc/group confirms it. One thing I have noticed is that the group fuse is listed in /etc/group but not /opt/ltsp/i386/etc/group would this be the cause of my problem?

Many Thanks

---

