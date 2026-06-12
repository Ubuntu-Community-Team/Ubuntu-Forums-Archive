---
title: "Monitor Dim to black workaround breaks Power management settings in (K)ubuntu 13.04"
date: 2013-05-02
forum: Desktop Environments
---

### Post by catseye2500 on 2013-05-02
System: Acer Aspire V3-771G-9456

Intel I7 Core-3632QM 2.2GHZ
6 gig memory 
120GB OGZ Solid State Drive
Nvidia Optimus-Geforce GT 640M with 2GB dedicated video memory

Kubuntu 12.10
Kernel 3.5.0-28
KDE 4.10.2

Kubuntu 13.04
Kernel 3.8.0-18
KDE 4.10.2

During boot up of live CD and after installation of both Kubuntu 12.10 and 13.04 my screen dims to black. I had to manually using the keyboard adjust the brightness for my screen to see. I found a solution to this by adding the following to my grub menu:

"acpi_backlight=vendor" so it looks like this in the menu: 

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
 
On both versions this allows me to boot up and the screen does not dim to black. 

The issue is for some reason, in Kubuntu 13.04 it breaks KDE power management settings so I can not dim the screen, suspend, or adjust the brightness of the monitor. When I take the acpi_backlight=vendor out of the grub menu the power management settings work fine in Kubuntu 13.04. I just have to manually adjust the brightness to login.

The odd thing is the above configurations works flawlessly in Kubuntu 12.10. I have the “acpi_backlight=vendor” in my grub menu and the power management setting work just fine.

BTW: I also did a fresh Install of Ubuntu 13.04 and it did the same as Kubuntu 13.04.


Any help will be appreciated...

---

