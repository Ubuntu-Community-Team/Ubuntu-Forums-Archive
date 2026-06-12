---
title: "Original N64 controller joystick does not work  in Mupen 64"
date: 2008-05-13
forum: Gaming &amp; Leisure
---

### Post by duramaxx2003 on 2008-05-13
I am using Ubuntu 8.04 and Mupen64 with the blights sdl plugin. My problem is that every button on my original N64 controller works except forward on the joystick. I have tried calibrating it per other guides out there for pc gamepads and have also tried 3 different N64 controllers. Is it in the calibration setup or what I'm lost.

---

### Post by acoustibop on 2008-05-14
If you've tried jscalibrator, duramaxx2003, this may be the cause of your problem.  It has a nasty habit of disabling the directional controls of controllers, while still reporting them as working.  The Kubuntu version, apparently works (as part of Kubuntu) but otherwise it's as I describe.

If you have (or have had) it installed, you need to remove the configuration as well as uninstall it, or the problem may continue to occur.

---

### Post by duramaxx2003 on 2008-05-14
yeah i tried jscalibrator and it would completely disable to joystick. I uninstalled it but am not sure where to find the configuartion file. Anyone help with the location of this file? Thanks again.

---

### Post by acoustibop on 2008-05-15
The best way to do it is to have the uninstall routine do it - in Synaptic you select 'Mark for complete removal' rather than 'Mark for removal' - there's probably a switch or command for apt-get, too, but I'm not sure what it is.

I don't have jscalibrator installed, obviously, but I would guess there may be a ~/.jscalibrator folder you can delete.

---

