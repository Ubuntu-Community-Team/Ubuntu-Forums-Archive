---
title: "GRUB related issue"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Bad2theBone on 2006-07-24
I had originally installed Ubuntu on my 2nd IDE HD. My 1st IDE HD had a SUSE 10.1 install on it. When I installed Ubuntu, I missed any part that allowed me to bypass the GRUB install and it got installed on my 2nd drive, which at first was a none issue. I then accidently partially disabled my SUSE install, which again was a none issue. My PC had x2 13GB HDDs on 1st IDE channel and x2 150GB SATA HDDs.

Problem starts when my grandson's PC HDD died, so I took my first IDE HD and installed it on his PC. Got it working so now that PC is up again. Then I did the physical change for my remaining IDE HD changing it to Single Master HD on 1st IDE channel. Then using my SystemRescue CD I mounted the boot part of the HD (/dev/hda1) and made the necessary changes to boot/grub/menu.lst so that everything from GRUB's perspective was now hd0,0 and the kernel's perspective was /dev/hda3. Unmounted drive rebooted to HDD and no booty, just a blank screen with flashing cursor in top left corner, not even the word GRUB. 

What do I need to do now? Do I need to reinstall GRUB? If so does Ubuntu have it's own version or is it just a vanilla flavor? And also is there a way to do it from CD instead of floppy as I don't have such an animal on my PC. Also what do I need to do to get my system back?](*,) 

TIA

---

