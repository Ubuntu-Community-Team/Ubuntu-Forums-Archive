---
title: "Lower mouse sensitivity below minimum?  (9.04)"
date: 2009-05-16
forum: Desktop Environments
---

### Post by djpandemonium on 2009-05-16
Apparently my gaming mouse is way too sensitive, because even with Sensitivity and Acceleration sliders all the way to "Low" under Mouse Preferences, it is much more sensitive than I can use comfortably (and much more sensitive than I'm able to set it in Windows).

Is it possible to lower mouse sensitivity below that?  Is there a config file somewhere I can edit, or something?

---

### Post by CrazyEye941 on 2010-03-17
I would like to know how to lower my sensitivity as well.

Same problem.

---

### Post by jtarin on 2010-08-25
> **CrazyEye941 said:**
> I would like to know how to lower my sensitivity as well.

Same problem.Kill small animals for starters.

---

### Post by M4he on 2010-08-26
I don't know if this will work in 9.04 since I'm using 10.04 but you could give the following a try:

in terminal type
```
xinput --list --short
```then note the name of your mouse. ("Razer DeathAdder" in my case)
and then type
```
xinput --set-prop "Razer DeathAdder" "Device Accel Constant Deceleration" 2
```(replace the "Razer DeathAdder" with the noted name of your mouse!)

Play around with the number at the end. 1 turns off the deceleration and increasing the number makes the pointer slower. 2 was sufficient in my case.

I then wrote a .sh script with the command and placed that in autostart, because this value isn't saved by default.

Good luck!

---

