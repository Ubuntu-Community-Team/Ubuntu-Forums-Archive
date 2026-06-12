---
title: "Multi-Monitors - Cursor Flickering/Freezing/Disappearing, GPU running at 100% Fan"
date: 2016-02-16
forum: Desktop Environments
---

### Post by hoffmann2 on 2016-02-16
Hey Guys,

I'm new to Ubuntu (literally just installed it an hour or so ago) and I've had a bit of an issue with my dual monitor setup.

Currently I am running a ASUS ROG Mars 760x2 - Which is two NVIDIA GTX 760 GPUs on one card. 
I did some digging around and I'm kind of caught in between two problems here. 

The default driver Ubuntu set me up with in the "Additional Drivers" tab, it is "X.Org X server - Nouveau display driver from xserver-xorg-video-nouveau (open source"
With this driver I am experiencing a multitude of problems, my mouse cursor is flickering, freezing and disappearing when I move it(on only one screen, it looks okay on the other) and my video card is running at what sounds like 100% fan speed. It is very loud.

I google the problem and it was suggested to switch to one of the other drivers, so I attempted to switch to NVIDIA binary driver - version 352.63 from nvidia-352 (proprietary, tested), and after doing so I was only seeing one screen.
I went into the NVIDIA settings, and enabled my second screen then restarted. This managed to get my screen to turn on, but it is just a black screen. When I move my cursor over to that screen I see a black X with a white outline as the cursor. 

Additionally, when I had the NVIDIA driver in use my second screen wasn't listed in the Screen Display settings.

How do I fix this?

For now I'll stick with the NVIDIA driver because my GPU isn't running at full fan speed (which I'm assuming means it isn't overheating) and the cursor doesn't flicker, but I hope I can find a way to get my second screen working. 

Thanks for your help here,

Hoffmann

---

### Post by hoffmann2 on 2016-02-16
Well, I managed to fix the problem by following this guide: [http://www.allaboutlinux.eu/remove-nouveau-and-install-nvidia-driver-in-ubuntu-15-04/2/](http://www.allaboutlinux.eu/remove-nouveau-and-install-nvidia-driver-in-ubuntu-15-04/2/) and manually installing the latest NVIDIA drivers, then re-enable the screen. 

Hopefully I did the right thing by doing this. Both my screens are working, there's no jitters and no problems thus far.

---

