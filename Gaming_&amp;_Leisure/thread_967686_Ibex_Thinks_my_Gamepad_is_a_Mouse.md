---
title: "Ibex Thinks my Gamepad is a Mouse"
date: 2008-11-02
forum: Gaming &amp; Leisure
---

### Post by ankursethi on 2008-11-02
It was working perfectly in Hardy, and now it's gone all insane. I just plugged my USB gamepad in, calibrated it with jscal, tested it out with the GUI based jscalibrator and was ready to kick alien butt.

Now jscal is recognising the gamepad, but not picking up any keypresses. Strangely enough, I'm able to move my mouse cursor in GNOME using the directional keys on my pad (but not able to actually click anything).

Now what?

---

### Post by Vadi on 2008-11-02
See if a bug report exists about this on Launchpad (possible with a workaround). If no, please report it.

---

### Post by greg.hagen on 2008-11-03
Same thing here. I'm so glad emulation works so well under the new opensource ati driver, but using a keyboard kinda ruins it.

---

### Post by register_sucks on 2008-11-03
Got the very same problem. I had never used a gamepad in Ubuntu before and spent ages wondering if I was gone mad.

God I'm so tired of the million issues with every single thing I want to get working in linux

---

### Post by Orfvz on 2008-11-04
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=953639]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=953639")

[https://help.ubuntu.com/community/Joystick_lshal_outputs_done]("https://help.ubuntu.com/community/Joystick_lshal_outputs_done")

---

### Post by Vadi on 2008-11-04
If you're on 64bit, someone made a .deb which supposedly works: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/284951/comments/13](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/284951/comments/13)

---

### Post by sirdilznik on 2008-11-04
> **Vadi said:**
> If you're on 64bit, someone made a .deb which supposedly works: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/284951/comments/13](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/284951/comments/13)

As a x86_64 Intrepid user I can confirm that the .deb in the link does indeed fix my gamepad issues (Logitech Wingman Action Pad) and works (so far) flawlessly. :KS

TORCS here I come again ;)

---

