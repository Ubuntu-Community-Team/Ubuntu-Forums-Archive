---
title: "Change vanilla Ubuntu to use LXDE instead?"
date: 2016-05-07
forum: Desktop Environments
---

### Post by unknown14 on 2016-05-07
Hi,

Just installed Ubuntu 16.0.4 on a skylake PC with intel graphics, pleasantly surprised at how easily it went on, but would like to change the look and feel to lxde?

---

### Post by sudodus on 2016-05-07
You can install **lxde** and select desktop environment at the log in screen.

```
sudo apt-get install lxde
```

But I think it is better to avoid messing with the installed system. Instead you can install a mini system into a USB pendrive or a virtual machine and do the testing there. See the following link

[Installation/UEFI-and-BIOS/stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative)

where you find how to get the compressed image file for a mini system with text screen user interface

**dd_text_16.04-UEFI-n-BIOS-4-pendrive-7.8GB.img.xz **

and what you can expect from it. One of the options in the installer submenu is to install LXDE, and it will give you a very light system (but not very polished). Lubuntu uses LXDE in a more polished way.

Please notice that it is a bad idea to mix Lubuntu and standard Ubuntu in your main installed system. It is OK in an experimental system, that you are prepared to overwrite with a new fresh installation.

---

