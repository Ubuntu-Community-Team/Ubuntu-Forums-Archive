---
title: "Kernel Images &amp; nVidia Drivers"
date: 2005-10-26
forum: Desktop Environments
---

### Post by SadaraX on 2005-10-26
Hello. I am having some trouble with using the premade kernel images because after I install them via apt-get, my video does not work. 

This is what I used originally to setup my video to work when I installed Breezy wth the original kernel that was installed when I installed Breezy from CD. 

```

apt-get install nvidia-glx nvidia-settings
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
nvidia-glx-config enable
vim /usr/share/applications/NVIDIA-Settings.desktop
Insert the following lines into the new file

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

```

Here is my hardware:
> 
Motherboard: EPOX EP-9NPA+Ultra NF4 ULTRA RT

Video Card: Geforce 6800GT 256MB DDR PCI Express x16 Video Card - ASUS EN6800/TD
/256
        Type VGA XFX|
        Model PVT45GUDF3

CPU: AMD Athlon 64 X2 4200+ Manchester 2000MHz FSB Socket 939 Dual Core
        Processor Model ADA4200BVBOX

RAM: CORSAIR XMS 1GB 184-Pin DDR SDRAM DDR 400 (PC 3200) Unbuffered System
        Memory Model CMX1024-3200C2PT
        Model #:CMX1024-3200C2PT


I am trying to use the apt-get kernel called "linux-image-2.6.12-9-686-smp". My system has an AMD64 chip, but I do not feel like moving to 64bit right now. 'uname -a' on my system reports:

 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux

So I am not sure if the 686-smp will work. However, there really are no other options for me via apt get. Like I said, after I apt-get the new kernel image and make sure the grub boot menu has its entry written properly, when I reboot no graphics show up. Help please.

---

### Post by astoltz on 2005-10-26
In addition to the kernel, you need to install the matching version of linux-resticted-modules. In your case, that would be linux-restricted-modules-2.6.12-9-686-smp.  You might have to re-install nvidia-glx also but try just the restricted-modules package first.

---

### Post by SadaraX on 2005-10-26
Thank you very much for the information. Doing a search has given me the options of 

linux-restricted-modules-2.6.12-9-686-smp
 or
linux-restricted-modules-2.6.12-9-686-smp-nvidia-legacy

What is better for me? What does nvidia-legacy do?

---

### Post by poofyhairguy on 2005-10-26
Moved to correct forum.

---

### Post by SadaraX on 2005-10-26
[QUOTE=poofyhairguy]Moved to correct forum.[/QUOTE]

Thanks, but I am doing this is Breezy. :) Not Hoary.

---

### Post by cbkm on 2005-10-27
[QUOTE=SadaraX]Thank you very much for the information. Doing a search has given me the options of 

linux-restricted-modules-2.6.12-9-686-smp
 or
linux-restricted-modules-2.6.12-9-686-smp-nvidia-legacy

What is better for me? What does nvidia-legacy do?[/QUOTE]

linux-restricted-modules-2.6.12-9-686-smp

nvidia-legacy is for graphics cards which are no longer supported by the unified driver.

---

### Post by SadaraX on 2005-11-05
The solution works great. Thanks

---

