---
title: "Tunnel video from a PC with no OS"
date: 2011-03-25
forum: Desktop Environments
---

### Post by varelov on 2011-03-25
I recently got a nice present from a friend of mine, a Dell Optiplex desktop with an empty hard disc on it, was told it only needs an OS since the HDD is wiped. So I turned it on and got no picture, however I got all other signs that everything else is working (POST beeping as usual). Oh man, my Ubuntu Install DVD is just waiting to be popped in since I intended to install Ubuntu on this PC.
I was wondering if there's any way to somehow tunnel the video output from this PC to another computer in the network. Mind that the video card may be gone (what I suspect since I get no picture on monitor) and that no OS is installed...
I was SO gonna turn it into an Ubuntu box without this hickup...

---

### Post by varelov on 2011-03-25
OK, kinda solved. The thing is this Dell PC has diagnostic lights (ABCD) at the back so you can diagnose what's the problem by looking at which lights are green and which are orange. After re-settling RAM modules, video is back but another problem persists- BIOS doesn't stop reporting that it can't find Primary Device 1 at which point I manually have to intervene by pressing F1 in order to make this PC boot into the fresh Ubuntu install.
This message kept showing despite changing jumper settings at the front of HDD. When I look at BIOS settings for hard disks, it is correctly recognized as a primary master. However, when I proceed with boot, that message appears again. 
Maybe the primary device HAS TO BE named "C:"?:lolflag:

---

