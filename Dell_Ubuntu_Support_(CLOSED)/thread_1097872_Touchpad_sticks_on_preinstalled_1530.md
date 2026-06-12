---
title: "Touchpad sticks on preinstalled 1530"
date: 2009-03-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by NCoachD on 2009-03-16
Hello

I have a preinstalled 1530, with a touchpad problem. Mostly the touchpad works, but every so often it sticks or moves intermittently for a few seconds. 

I know the touchpad on Ubuntu has problems, but has anyone come across this on the 1530? and what can be done?

Thanks

---

### Post by jespdj on 2009-03-17
I have never had any problem with the touchpad so that it "sticks". The touchpad works fine for me (with 64-bit Ubuntu 8.04), but I had to add a kernel parameter:
```
i8042.nomux=1
```
as described [here](http://ubuntuforums.org/showthread.php?t=737060) to make it work properly. Without this, the mouse pointer jumps like mad.

Which BIOS version do you have? I have A12.

---

### Post by NCoachD on 2009-03-17
I have Bios A12 for 32bit Ubuntu 8.04

---

