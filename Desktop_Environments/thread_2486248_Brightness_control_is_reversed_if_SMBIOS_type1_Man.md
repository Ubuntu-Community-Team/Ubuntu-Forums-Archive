---
title: "Brightness control is reversed if SMBIOS type1 Manufacturer string with a space"
date: 2023-04-24
forum: Desktop Environments
---

### Post by ginousi on 2023-04-24
We encounter the e-DP brightness control bar action is reversed, 
if SMBIOS data type1 Manufacturer string with a space...

For example, if type1 string is "New Corporation", the brightness control bar action will be reversed.
if type1 string is "NewCorporation", the brightness control bar action will work fine.

[IMG]https://i.imgur.com/OQHMj39.jpg[/IMG]

it is a known issue?
or how to fix(avoid) this issue if type1 string with a space is needed?


Thanks

---

### Post by idmbe on 2023-04-24
Hello, 

type this via terminal then paste results here:

uname -v

lspci | grep VGA

---

### Post by ginousi on 2023-04-25
[IMG]https://i.imgur.com/9JK5CgE.png[/IMG]

---

### Post by idmbe on 2023-04-25
look here, that will help you i hope:
[https://wiki.ubuntu.com/Kernel/Debugging/Backlight](https://wiki.ubuntu.com/Kernel/Debugging/Backlight)

---

### Post by ginousi on 2023-05-04
We has a workaround to fix this issue.

1. Edit /etc/default/grub file.
2. Add i915.invert_brightness=-1 to the "GRUB_CMDLINE_LINUX_DEFAULT"
3. Run sudo update-grub2 (or sudo update-grub) and reboot.

[IMG]https://i.imgur.com/VKyeDZ1.jpg[/IMG]

---

