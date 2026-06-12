---
title: "Ubuntu 11.04 screen resolution"
date: 2011-06-30
forum: Desktop Environments
---

### Post by netsense on 2011-06-30
I just converted an Atom D525 (NM10) desktop I built from Kubuntu 10.04 to Ubuntu 11.04, to sample the Unity Desktop. I like unity, but the problem I now have is that the monitor configuration utility in System Settings lists resolutions only up to 1024x768, whilst Kubuntu ran comfortably at 1280x1024.

I ran xradr, and it showed the higher reolution, but switching to it from xrandr broke the desktop, and I had to hard reboot.

It doesn't seem that Unity uses an xorg.conf file, so I can't change that.

Can anyone help?

Edwin

---

### Post by wildmanne39 on 2011-06-30
> **netsense said:**
> I just converted an Atom D525 (NM10) desktop I built from Kubuntu 10.04 to Ubuntu 11.04, to sample the Unity Desktop. I like unity, but the problem I now have is that the monitor configuration utility in System Settings lists resolutions only up to 1024x768, whilst Kubuntu ran comfortably at 1280x1024.

I ran xradr, and it showed the higher reolution, but switching to it from xrandr broke the desktop, and I had to hard reboot.

It doesn't seem that Unity uses an xorg.conf file, so I can't change that.

Can anyone help?

EdwinHi, try this link.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by netsense on 2011-07-01
> **wildmanne39 said:**
> Hi, try this link.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)


OK, I got the resolution to change, but the desktop background has a 1024x768 image overlayed over the 1280x1024 image, and the launcher (if that's the right term) is limited to 769px high!

---

### Post by wildmanne39 on 2011-07-01
> **netsense said:**
> OK, I got the resolution to change, but the desktop background has a 1024x768 image overlayed over the 1280x1024 image, and the launcher (if that's the right term) is limited to 769px high!
Hi, can you post a screenshot? did you do a fresh install of 11.04 ubuntu  by wiping out kubuntu first?

---

