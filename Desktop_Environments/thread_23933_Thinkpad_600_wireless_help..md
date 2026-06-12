---
title: "Thinkpad 600 wireless help."
date: 2005-04-04
forum: Desktop Environments
---

### Post by AMP on 2005-04-04
I have the ndiswrapper latest debian package copyed on to my HDD at /home/andrew/, and i was wondering what cmds do i do after dkpg -i and how should i go about setting up my belkin card for my cardbus on my laptop?
I also have the tar file, and anything i can copy and paste is PERFECT.
 :mrgreen:

Also i reconfigured my xserver so no i can make my resolutions go higher than 800by600, but when i try to change it in Gnome it only lets me go to 800by600.

---

### Post by gotaserena on 2005-12-20
Does "acx_pci" support your card? I've got my card working in no time using it instead of ndiswrapper.

About the screen resolution you need to set the default bpp to 16 in /etc/X11/xorg.conf.

---

### Post by bsj on 2006-01-01
Happy New Year to all! This is my first post to the forums. I've been using kubuntu for about 6 months. :smile: 

I actually have a TP 600E. I am having an incredibly hard time getting the AirLink 101 AWLC3025 working properly. I've tried House of Craig's intructions. It would seem that I don't need to compile the driver (acx_pci). Everything seems to load fine. I'm on a Winblows machine right now, so I can't give you the precise output.

iwconfig has 0's for the access point.
ifconfig shows wlan0 as up with no ip address.
iwlist wlan0 scan gives no scan results.

lspci shows Ti ACX 111 chipset.

I have disabled acpi in the boot parameters in grub.

I'm not sure where to go from here. I've gathered from searching the forums here and at Gentoo that the TP 600E has some IRQ issues. Is there a way to manually assign an IRQ to my card?

Any help is appreciated.

---

### Post by bsj on 2006-01-01
Never mind! I got it going. It seems that my /boot/grub/menu.lst file was changed back to the default. Not sure how. Maybe I didn't save it properly before. Regardless, this addition to the kernel line is essential for the tp 600E owner:

acpi=off

the airlink pcmcia card works now.

---

