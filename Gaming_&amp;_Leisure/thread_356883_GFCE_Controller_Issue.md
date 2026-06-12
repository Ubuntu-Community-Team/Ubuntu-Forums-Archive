---
title: "GFCE Controller Issue"
date: 2007-02-08
forum: Gaming &amp; Leisure
---

### Post by fhco on 2007-02-08
Ok, I've got the NES emulator GFCE up and running. ROMs load fine, sound and video are perfect. I am using a USB controller, and I have installed *jscalibrator*, which recognized my controller perfectly.

My problem: When I go to configure Gamepad #1 in GFCE, all the buttons are recognized *except* for the directional pad. I can successfully map all keys on my controller - even the analog keys (not moving them for direction, but pressing them as a button) - but when I press the d-pad, GFCE simply doesn't recognize it.

Any ideas? :(

I should also mention that the same thing happens in ZSNES, so apparently it's not a GFCE problem. But in jscalibrator, the directional pad is recognized...

---

### Post by SBFC on 2007-04-28
Not to make a zombie thread of this...but were you able to resolve this? I have the same problem.

---

### Post by DoktorSeven on 2007-04-28
Does doing this:

**sudo rmmod analog**

fix the problem?  I had the same issue with my gamepad and that made it work.

---

### Post by SBFC on 2007-04-29
Intersting thing...bear in mind the analog module was loaded prior to this.

I removed it like you suggested, and then nothing worked. So I readded it with 'sudo modprobe analog'....and now...everything works...yeah...weird.

---

### Post by skralljt on 2008-02-21
I also have this problem, because it seems to work fine in jscalibrator, I believe this must be an issue with gfceu.

---

### Post by acoustibop on 2008-02-21
No, it's an issue with jscalibrator, skralljt. It has a nasty habit of disabling the directional controls of controllers while still reporting them as working.  Apparently, the native Kubuntu version works Ok.

When you remove it, make sure you remove the configuration as well, or the effects may persist.

You shouldn't really need calibration for a USB controller - if you do, there's joystick (also in the repositories).  This package installs 2 command line utilities, jscal and jstest.

---

