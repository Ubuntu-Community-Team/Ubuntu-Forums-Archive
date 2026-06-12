---
title: "screen brightness ubuntu 11.10"
date: 2011-10-30
forum: Desktop Environments
---

### Post by Taoufiks on 2011-10-30
hi!
I have a toshiba satellite L755 PC
 Core i5
 6GB RAM
 Nvidia Geforce 2GB
I have installed Ubuntu 11.10 on dual boot.... 
but I can't set the screen brightness.... and the FN key don't works 
what should I do?

---

### Post by Toz on 2011-11-04
Have you installed the proprietary nvidia drivers? If so, try adding the following:
```
Option "RegistryDwords" "EnableBrightnessControl = 1" 
```
...in the device section of your /etc/X11/xorg.conf file and rebooting.

Barring that there is always the fnfxd & fnfx-client utilities:
> Description-en: ACPI and hotkey daemon for Toshiba laptops
 fnfx enables owners of Toshiba laptops to change the LCD brightness,
 control, the internal fan and use the special keys on their keyboard
 (Fn-x combinations, hot-keys). The internal functions will give the
 possibility to map the Fn-Keys to functions like volume up/down, mute,
 suspend to disk, suspend to ram and switch LCD/CRT/TV-out. These
 functions heavily depend on the system and/or kernel configuration.
 You will need at least a kernel (v2.4.x, v2.5.x, v2.6.x) with ACPI and
 Toshiba support (CONFIG_ACPI and CONFIG_ACPI_TOSHIBA).

They are available in the Software Center for installation.

---

### Post by Taoufiks on 2011-11-06
hi thank you pro, it works fine for me :P
after rebooting the computer :)
then a have installed a screen brightness indicator and all is fine 
thank you!

---

