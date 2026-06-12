---
title: "Radeon 4850 + which driver = compiz working?"
date: 2009-10-18
forum: Desktop Environments
---

### Post by Blufires on 2009-10-18
Hi, sorry that I'm asking a question which (from my spending about 8 hours today searching) has been around since release 7.02ish, but I really can't figure this out.

I've just made the switch from Vista to Ubuntu 9.04 and I'm glad I did, everything "just worked" out-of-the-box, even a graphics driver started working on it's own. However, if I selected the "normal" or "extra" visual effects options, I would be prompted to install an nVidia driver of some sort (xserver?:S). I installed this, thinking that it would go away once it realised that only the useless onboard video chip is nVidia, but the visual effects still opened the driver download. I installed the cataylst driver from amd's internet site and thought this should work. It still didn't. I searched the internet for hours and tried a few terminal commands to disable xorg, xserver etc... Now I'm just lost, I don't know which driver is which anymore, is there just the AMD one and the xorg open source one? Or is there a 3rd one called xserver. Is xserver an nVidia specific driver or a part of gnome?

Any help would be greatly appreciated, and again, sorry for the noobiness, but I need somewhere to start to enter the open source comunity. If somebody could just give me a rundown of what each name refers to (xorg, xserver etc.) and explain which drivers work with compiz and which do not, I would be very greatful. I assure you I was a pro on windows :P

P.S. As a new windows boat-jumper I don't know much about the terminal language/commands, though I have worked out the whole "sudo" thing and how to launch a program as a super-user now...

EDIT: O.K. Fixed the problem, I had to reinstall the AMD catalyst Control Center driver (which includes the open source driver that compiz needs) but choose custom this time and make sure that the kernel driver option was checked.

---

