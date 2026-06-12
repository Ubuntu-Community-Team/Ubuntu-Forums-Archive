---
title: "Gamepad calibration"
date: 2008-02-06
forum: Gaming &amp; Leisure
---

### Post by raptor222 on 2008-02-06
Hi, I have a generic ps2 like game pad (for PC computers) and the joystick calibration tool (the only one available in the Ubuntu repositories) doesn't calibrates it correctly, it identifies all the axis but doesn't assigns them correctly.
so i was wondering if there is another tool/driver for this.

---

### Post by disturbedite on 2008-02-06
with kde & my universal usb converter hub i just plugged in my xbox controller & never had to calibrate anything.
kde's joystick/pad config is a built in module of system settings.  you can do it from there.
but i don't know about gnome.
i posted that just in case you happen to use kde.

---

### Post by raptor222 on 2008-02-06
i dont use KDE and i think that i i had a x-box controller or a brand name (mine is just generic noname (tunsen if you were wondering) gamepad.

---

### Post by acoustibop on 2008-02-06
There are actually two joystick calibration packages in the repositories, jscalibrator, which has a GUI, and joystick, which consists of two command line apps, jstest and jscal.

I would advise against using jscalibrator.  It's apparently the same application that Kubuntu includes natively but, while it apparently works fine in Kubuntu, it messes up in Ubuntu - it has a nasty habit of disabling directional controls for other applications, while reporting them as working.  If you have it installed, remove it including the configuration files.

As disturbedite says, it's not normally necessary to calibrate a USB controller unless you have a specific problem with it.

---

### Post by raptor222 on 2008-02-06
Thaks for the advice!
but i want to test if it (the gamepad) works and dont have how

---

### Post by acoustibop on 2008-02-06
Try the jstest module of joystick then, raptor222.

---

