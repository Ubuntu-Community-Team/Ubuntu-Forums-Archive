---
title: "SNES Controller"
date: 2007-03-26
forum: Gaming &amp; Leisure
---

### Post by carlosjoan91 on 2007-03-26
Hi, i made a SNES-parallel port adapter, that works nicely in windows... and after loading the modules, in linux in the joystick calibration utility, also works nicely, however, i tried it in zsnes and in snes9x and they don't detect the axis movements (the axis movement appear fine in the joystick test/calibration) so, are the axuis supported by those emulators? if not, isn't there a tool or utility that could translate joystick movement/buttons into keypresses, in windows there is something called joytokey, isn't there something similar here? thank you

---

### Post by MonkeyBoy on 2007-03-26
Joy2key claims to be able to do that and it is in the repos.

Good luck.  It sounds cool.

---

### Post by grossaffe on 2008-02-11
I also have an SNES-Parallel connector i use and it works just fine in ubuntu, but i do have a question.  is there any way to get this to work with a USB-parallel cable?  My laptop does not have a parallel port which kinda sucks because that's my traveling emulator.

---

### Post by acoustibop on 2008-02-12
Is the "the joystick test/calibration" jscalibrator, carlosjoan91?  In that case, it may well be your problem: uninstall it, including the configuration.  It has a nice little habit of disabling directional controls in joysticks/controllers, while still showing them as working.

Apparently the version that's native to Kubuntu is Ok, but not otherwise.  If you want a joystick calibrator (not really necessary, usually) try joystick, also in the repositories.  It consists of 2 command line applications, jscal and jstest - just enter either of those in a terminal after installing for its instructions list.

---

