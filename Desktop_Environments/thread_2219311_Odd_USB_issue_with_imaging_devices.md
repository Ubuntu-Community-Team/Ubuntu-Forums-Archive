---
title: "Odd USB issue with imaging devices"
date: 2014-04-23
forum: Desktop Environments
---

### Post by LVDave on 2014-04-23
I recently rolled out a Dell Latitude D620 with XUbuntu 12.04 installed. The user in question has an HP Deskjet 2512 printer/scanner and a Nikon Coolpix L22, both of which were detected and worked fine when the system was given to the user, about a month ago. Today she calls and says she cannot scan. A check with lsusb shows the HP device is there. The HPLIP system was already installed on the machine, but with this weirdness.. The HP device is not seen by HPLIP, nor can it be detected by HPLIP, even with the "manual configuration" where you enter the device id from lsusb. I figured something was off with HPLIP, but when the user asked me to download new pix from her Nikon camera, I found that it, too, was seen in lsusb, but F-spot does not see it. Since the machine was set for automatic updates, it appears that one or more updates has partially broken USB, at least for imaging devices. Is there any way to see what updates have been applied, and more importantly, to roll back any that bork USB? I've used Linux/Ubuntu for a long time, but have never run into an issue like this...
Its unknown if the printer functionality on the HP AIO works as the user does not have any print cartridges for it, and does not intend to use the printer function..

---

