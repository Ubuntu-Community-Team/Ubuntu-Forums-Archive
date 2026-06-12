---
title: "bus mouse won't work"
date: 2005-08-01
forum: Desktop Environments
---

### Post by WildWillie on 2005-08-01
I went through dpkg-reconfigure xserver-xorg to set everything up and all was well, in that the desktop finally loaded. Unfortunately, the mouse won't work. I set it to the correct port (I only have 1 serial so it's serial 1 right?) and so far as I know everything is correct. Any advice?

---

### Post by heimo on 2005-08-02
First serial port is device /dev/ttyS0
[https://wiki.ubuntu.com//SerialMouseHowto](https://wiki.ubuntu.com//SerialMouseHowto)

Can you copy paste the section with mouse setting from your /etc/X11/xorg.conf?

---

