---
title: "Turn off touchpad on ThinkPad?"
date: 2015-10-08
forum: Desktop Environments
---

### Post by drfox on 2015-10-08
In XFCE/Xubuntu, it is possible to turn off the touchpad and just have the pointer and touchpad buttons work on a ThinkPad.
Is it somehow possible to do the same with Gnome 3.16 or 3.18?
Thanks, Larry

---

### Post by ajgreeny on 2015-10-08
Try command ```
synclient TouchpadOff=1
``` to turn it off and ```
synclient TouchpadOff=0
```to turn it on again.

The command synclient can do a lot more than that so see [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by drfox on 2015-10-08
> **ajgreeny said:**
> Try command ```
synclient TouchpadOff=1
``` to turn it off and ```
synclient TouchpadOff=0
```to turn it on again.

The command synclient can do a lot more than that so see [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Great information, thanks very much!

---

### Post by cloud95728 on 2015-10-18
go into the bios for that

---

### Post by vasa1 on 2015-10-18
> **cloud95728 said:**
> go into the bios for that
Why? ajgreeny has provided an answer. OP is okay with it. So why are you suggesting going into the BIOS?

---

