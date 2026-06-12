---
title: "how to make display #2 the 'left' / 'main' display in multi display setup?"
date: 2011-12-13
forum: Desktop Environments
---

### Post by akos.maroy on 2011-12-13
Hi,

I'm trying to set up my laptop with an external monitor, where my monitor is left of the laptop. Thus, I'm looking for a solution where the external monitor is the 'main' monitor, with the Unity bar on the left, etc., and my laptop monitor is to the 'right', all in a single display.

I have an HP Envy 15 laptop with an ATI Moblity Radeon HD 5800 video card, and I'm using the proprietary ATI driver version 8.84.6, and Ubuntu 11.04 x86_64.

Using the Catalyst control center, I can set up both monitors. Setting to 'clone' mode 'just works. the laptops own screen in identified as display #1, while the external monitor is display #2, which is quite logical. both sport a 1920x1080 native resolution.

I can also set up a multi-display desktop with these displays, and I can play with the catalyst control center UI so that display #2 is 'on the left', and display #1 is on the right. after hitting Apply, it tells me to reboot. I reboot fine, and while indeed, the external display will be the 'left' side of the desktop, the main display remains the laptop display. the Unity bar is displayed there, and new windows pop up there. also, when hitting the Unity 'application choser', it is displayed on the laptop screen.

Is there a way to make Unity understand that display #2, which is the left-most display, is the 'main' / 'primary' display?

Akos


PS: As an alternative approach, I tried to configure Xinerama, but that will basically break logging in (the same user just won't log in, but the login screen is displayed again and again). the only remedy is to set Xinerama to 'off' in xorg.conf manually.

PPS: I'm using 11.04 and not 11.10, because 11.10 won't boot on my laptop, see [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/876436](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/876436)

---

