---
title: "PCI: Cannot allocate resource region 1 of device 0000:00:14.0"
date: 2007-10-30
forum: Dell  Ubuntu Support
---

### Post by Ismail on 2007-10-30
[COLOR="Black"][B]Hi,

i am installing UBuntu 7.10 downloaded from net on Dell Optiplex 320 i am faceing Error(PCI: Cannot allocate resource region 1 of device 0000:00:14.0) after that the screen will stuck and i cant do any thing. if some body knows about that error pleae mail me on my personal address.:KS

[email]ismail@megaplus.com.af[/email]


Thanks & Regards
Muhammd Ismail[/B][/COLOR]

---

### Post by teqagogo on 2007-11-07
Hi,

I got the same problem with both 7.04 and 7.10. Toshiba psp3ae

Here is how to fix the sound and the PCI error messages at startup:

1/ Kernel startup option
sudo cp -p /boot/grub/menu.lst /boot/grub/menu.lst.bck
vi /boot/grub/menu.lst
and add the option acpi=off to the kernel
you should have something similar to:
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=XXXXXXXXXXXXXXXXXXXXXXX ro quiet splash acpi=off


2/ Re-configure the alsa driver

there are several ways to so that, i tried the classic method (if you want to there are a lot of forums describing this, go first to alsa web site)but found this one on a forum which is working fine:

first get this tool:
sudo apt-get install module-assistant

Then :
cd /usr/src
sudo module-assistant update
sudo module-assistant prepare
sudo module-assistant auto-install alsa
sudo shutdown -r now

Hope you hear the welcome tam tam

:)

---

