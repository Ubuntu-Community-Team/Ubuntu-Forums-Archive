---
title: "KVM not working properly in 12.04"
date: 2012-08-14
forum: Desktop Environments
---

### Post by toontu on 2012-08-14
Hi,

I have two desktops both running Ubuntu, not the same version though. I use KVM so that I can jump between the two without having extra peripherals. It worked very well in the previous versions of Ubuntu. But ever since I upgraded one of the desktops to 12.04, bad things come. Basically, the 12.04 desktop will stop sending signals to the screen after I switch to the other desktop. The other one is fine.

I mainly use the 12.04 desktop and ssh to the other one but occasionally I need to switch to the other one.

This is quite annoying. Is it something to do with the graphic card driver or something else?

Any advice is appreciated. Cheers.

---

### Post by kansasnoob on 2012-08-15
Might it be this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/988290](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/988290)

If so it might help a little to mark it effects me too. I'm not very satisfied with any of the work-arounds mentioned there but I hope to increase the heat on that bug enough to get it fixed :)

---

### Post by toontu on 2012-08-15
Thanks, kansasnoob. It looks quite relevant. I am also experiencing the resolution change issue. Just sometimes, it's changing the resolution and some other time, it's going blank completely and becomes unresponsive.

Anyway, I tried one of the workarounds mentioned in the page you posted, which is purge gnome-screensaver. It works OK for me. So far, the screen doesn't go blank any more, but resolution change is still occurring. Well, that's a good step forward for me. Hope the bug can be fixed asap.

Many thanks for your help. Have a good day.

---

