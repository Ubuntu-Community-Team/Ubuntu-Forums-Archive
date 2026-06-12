---
title: "Nvidia drivers not working after updates (!?)"
date: 2009-01-09
forum: General Help
---

### Post by Pauligrinder on 2009-01-09
Hello.

I installed the latest updates yesterday (some kernel stuff etc, can't remember what exactly), and then I rebooted. After that, my graphics card won't work anymore! Before showing the login, it says something like "kinit failed", and "couldn't find previous boot image" or something like that. And then there was something about a hard drives UID, it flashes by very quickly, so I can't remember all of it. Anyways, after examining the UID, I found that it is the UID of my primary HD, where Xubuntu (8.04.1 by the way) is installed. 
[CORRECTION]:
It says "kinit couldn't find something in UID ...." and then "searching for resume image in UID ...." and then "no resume image found, doing normal boot"
After that, it gives me the "your graphics card and display could not be detected" thing. I've tried to remove some graphics related packages to see if that would've been the problem, but nothing changed.
I'm starting to have a feeling that this problem may be related to my BIOS. A few of my HD's keep changing places (sda and sdd to be specific). It seems like it's trying to read the graphics configuration from another HD or something like that. Another interesting thing is, that if I edit my BIOS configuration to make it boot only from the main HD, it won't boot! Are my boot files on another HD?
Some specs, in case they are needed:

Motherboard: Asrock P4V88+
CPU: Intel Pentium 4 3,0 ghz
Graphics: Nvidia Geforce 7600 GT (256mb) (AGP)
Main HDD: Samsung 300gb SATA2, with jumper to dissable SATA2 and go into SATA1 mode (MoBo doesn't support SATA2)

---

### Post by stchman on 2009-01-09
The reason is that the drivers you installed only attached themselves to the current kernel.

When you upgraded to a new kernel then the modules did not transfer to the new kernel.

I recommend that you simply enable the restricted drivers.  I have a 7600GT and it works perfectly under Ubuntu 8.04.

---

### Post by Pauligrinder on 2009-01-09
Thanks for the quick reply. Enabling the restricted drivers directly didn't fix the graphics, but I don't get the kinit-thing anymore, which is at least a step forward. 
It seems like the modules are still being made into the wrong kernel - when I'm installing drivers downloaded from nvidia, it detects 180.22 installed, and not the one (169.xx) I installed through Xubuntus restricted drivers app. What should I do now?

Ok, so I tried with the previous kernel, which was working 100% until yesterday... And guess what! The same thing happened, even the kinit thing came up on startup... I don't get it.
The kernel version is 2.6.24-23 btw (the new one), and the previous one was 2.6.24-22, in case that'd help...

---

### Post by Pauligrinder on 2009-01-09
Yay, I got it to work again :)

I messed around with it a lot, ultimately removing all files having anything to do with nvidia. Then, I installed the latest drivers (180.22) from the website, and rebooted. And wohoo, the NVIDIA logo came up! Now I'm going to remove the restricted drivers app, I prefer to install them manualy anyway.

---

### Post by voxman69 on 2009-01-17
Thank you Pauligrinder!!
Had the same problem as you and followed your instruction. Now all is good in the world again! :-)

---

### Post by sdennie on 2009-01-17
To prevent this problem in the future on Hardy, use: [ HOWTO: Automatically update manually installed NVidia drivers after kernel updates]("http://ubuntuforums.org/showthread.php?t=835573")

---

### Post by voxman69 on 2009-01-17
Brilliant sdennie! Thanks a lot!!

---

