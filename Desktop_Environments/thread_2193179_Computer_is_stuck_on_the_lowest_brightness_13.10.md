---
title: "Computer is stuck on the lowest brightness 13.10"
date: 2013-12-11
forum: Desktop Environments
---

### Post by miguelmendes1997 on 2013-12-11
Well I recently did a dual boot of windows 7 with Ubuntu 13.10, everything is going well and I'm really liking it. However I cannot control brightness which is stuck in it's lowest setting.
I tried xbacklight, updated the drivers, change the grub file and nothing has solved the problem. When I do "Fn + uparrow" it shows the brightness control and it moves but nothing happens on the screen. I'm really getting frustrated.

Computer Specs:

Samsung RV520
4Gb of RAM
160Gb drive for ubuntu
running ubuntu 13.10

Thank you!

---

### Post by Toz on 2013-12-11
Hello and welcome to the forums.

Can you open a terminal window, run the following commands and post back the results:
```
cat /proc/cmdline
```
```
lspci -k | grep -iA2 VGA
```
```
for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
```
```
cat /var/log/Xorg.0.log | grep -i backlight
```

This will give us more detailed information about your video card(s), backlight interfaces and kernel configuration.

---

### Post by miguelmendes1997 on 2013-12-11
> **Toz said:**
> Hello and welcome to the forums.

Can you open a terminal window, run the following commands and post back the results:
```
cat /proc/cmdline
```
```
lspci -k | grep -iA2 VGA
```
```
for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
```
```
cat /var/log/Xorg.0.log | grep -i backlight
```

This will give us more detailed information about your video card(s), backlight interfaces and kernel configuration.

**cat /proc/cmdline**
BOOT_IMAGE=/vmlinuz-3.11.0-14-generic root=UUID=48fd919b-32d4-4b8b-bd71-dc92d90bd472 ro quiet splash "acpi_osi=!Windows 2012" acpi_backlight=vendor

**lspci -k | grep -iA2 VGA**
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [GeForce GT 520M] (rev a1)
    Subsystem: Samsung Electronics Co Ltd Device c597
    Kernel driver in use: nvidia

**for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done**
/sys/class/backlight/samsung
0
8

**cat /var/log/Xorg.0.log | grep -i backlight**
[    23.240] Kernel command line: BOOT_IMAGE=/vmlinuz-3.11.0-14-generic root=UUID=48fd919b-32d4-4b8b-bd71-dc92d90bd472 ro quiet splash "acpi_osi=!Windows 2012" acpi_backlight=vendor

---

### Post by Toz on 2013-12-11
Try adding:
```
Option         "RegistryDwords" "EnableBrightnessControl=1"
```
...to the **Device** section of your **/etc/X11/xorg.conf** file and logging out and back in again.

If you don't have an /etc/X11/xorg.conf file, create the file **/usr/share/X11/xorg.conf.d/10-nvidia-brightness.conf** with the following content:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 520M"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```
...and log out and back in again.

And if that doesn't work, can you post back the contents of the file (/etc/X11/xorg.conf OR /usr/share/X11/xorg.conf.d/10-nvidia-brightness.conf) that you created?

---

### Post by miguelmendes1997 on 2013-12-11
messing with the xorg.conf made my pc crash and display the "System is running on low graphics" Error message, I managed do fix it, however the xorg.conf was empty, I don't know if it is supposed to have something in there...

---

### Post by Toz on 2013-12-11
> **miguelmendes1997 said:**
> messing with the xorg.conf made my pc crash and display the "System is running on low graphics" Error message, I managed do fix it, however the xorg.conf was empty, I don't know if it is supposed to have something in there...

The xorg.conf file was empty when you started? If so, then you should add that code to /usr/share/X11/xorg.conf.d/10-nvidia-brightness.conf.

Can you re-run the commands from post #2 again?

---

### Post by miguelmendes1997 on 2013-12-11
Well before you posted this I realized that I actually had no xorg.conf file (noobish me...) and tried the second option you mentioned, gess what, problem solved! Thank You!

---

### Post by Toz on 2013-12-11
> **miguelmendes1997 said:**
> Well before you posted this I realized that I actually had no xorg.conf file (noobish me...) and tried the second option you mentioned, gess what, problem solved! Thank You!

Glad to hear. If you don't mind, can you mark this thread SOLVED using the "Thread Tools" link above? Thanks.

---

### Post by miguelmendes1997 on 2013-12-11
Sure :D

---

