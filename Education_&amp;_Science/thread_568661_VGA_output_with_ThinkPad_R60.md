---
title: "VGA output with ThinkPad R60"
date: 2007-10-06
forum: Education &amp; Science
---

### Post by Wittgenstein on 2007-10-06
*I've tried this one in Hardware/Laptops and Absolute beginner talk without any response. I'll give it one last try here:*

Hi, I have a ThinkPad R 60 running Feisty, and the graphical card is an Intel Graphic Media Accelerator 950. I don't seem to be able to connect to a projector or external monitor using the VGA port. There are a lot of Howtos out there, and most of them involves some kind of changing of the xorg.conf. Do I have to change the file or is there some other solution (my Fn keys don't seem to work)

I would like to now the easiest way to get this functionality working - it's essential when using the computer in front of an audience and I don't see the point with OpenOffice Impress if you can't use a projector!

---

### Post by kleeman on 2007-10-06
A great site for thinkpad problems is thinkwiki. Your issue seems to be mentioned here:

[http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950](http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950)

It appears you will need to edit your xorg.conf file

I would try this (from the link above)

Here is the relevant text for running the VGA port as a true clone (so even things like Xine video playback appears on both screens) of the internal LCD display:

   Section "Device"
        Identifier "Videocard0"
        Driver "i810"
        BusID "PCI:0:2:0"
        Option "MonitorLayout" "NONE,LFP+CRT"
        Option "DevicePresence" "true"
        Option "CheckLid" "false"
        VendorName "Lenovo"
        BoardName "Intel Corporation Mobile Integrated Graphics Controller"
   EndSection

Reboot after altering xorg.conf. Also BACKUP YOUR OLD xorg.conf IN CASE SOMETHING GOES WRONG!!!!

---

### Post by Wittgenstein on 2007-10-10
Thank you so much - it worked!! My xorg.conf said:

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

When changing Identifier to Videocard0 Linux was not able to run X. When keeping Identifier as it was and changing the rest like you wrote, it works perfectly.

(I've seen the ThinkWiki page too, but I was a little afraid of changing the xorg.conf file.)

---

