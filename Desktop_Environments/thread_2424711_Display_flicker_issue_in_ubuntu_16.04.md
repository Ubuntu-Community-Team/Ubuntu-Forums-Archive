---
title: "Display flicker issue in ubuntu 16.04"
date: 2019-08-13
forum: Desktop Environments
---

### Post by pxl29 on 2019-08-13
Hello, 

Recently i encountered a problem with the display in lenovo z5070 laptop. At the start it is normal, then after some time left half of the display show some flicker and disappear. 
But then (i don't know what is triggering this) suddently left half of the display is full of black and white barcode image and I can't see anything. So I can work only on right half of the display.

If i restart my pc ,everything is normal again.

---

### Post by Autodave on 2019-08-13
Sounds to me like your display or cabling for your display is failing.  Can you hook-up an external monitor to the laptop and see if it has the same issue?

---

### Post by &amp;wP*!) on 2019-08-14
Also type following commands, what do they give ?
```
echo $XDG_SESSION_TYPE
echo $XDG_CURRENT_DESKTOP

```
I assume you have an Intel CPU with the integrated HD 4400 graphics. Try following: Add **i915.enable_psr=0** to **GRUB_CMDLINE_LINUX_DEFAULT** in **/etc/default/grub** file. Run **grub-mkconfig -o /boot/grub/grub.cfg** (assuming your GRUB file is there). Reboot.

Kernel 5.2.8 fixes a very similar problem. However Ubuntu ships this solution earliest in 19.10 (October) or you install 5.2.8 by yourself until then.

---

