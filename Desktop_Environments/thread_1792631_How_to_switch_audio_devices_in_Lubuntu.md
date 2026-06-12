---
title: "How to switch audio devices in Lubuntu?"
date: 2011-06-28
forum: Desktop Environments
---

### Post by puntigamer on 2011-06-28
Hi folks,
I've an older PC, and I would like to use it with Lubuntu, because it's much faster than Ubuntu or Win XP (excuse me for the comparison). The only thing that prevents me from using Lubuntu is that I can't find any application to switch the sound card!
How can I switch audio devices from Lubuntu?

Thanks in advice!

---

### Post by ajgreeny on 2011-06-28
Run ```
alsamixer
``` in terminal to check levels of outputs, and using F6 change sound card

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

---

### Post by puntigamer on 2011-06-28
I will give it a try, thank you. If I save it, will it be saved forever, right?

---

### Post by ajgreeny on 2011-06-28
> **puntigamer said:**
> I will give it a try, thank you. If I save it, will it be saved forever, right?
I think so, but having never used alsamixer for this, I'm not totally sure.

---

### Post by JC Cheloven on 2011-06-28
You may want to permanently disable one of them (the "bad one", most likely the integrated sound chip in your motherboard) and always use the "good one", as the only one the system sees. 

It can be done by blacklisting the module ("driver") of that "bad" card so that it's not loaded into the kernel. 
For example, I have a "good" RME Hammerfall pci card, and the typical low-end intel sound chipset. I edited /etc/modprobe.d/blacklist.conf to add this line at the end:
```
blacklist snd_hda_intel
```

Of course "permanently" means as long as you don't edit back this file.
Using LUbuntu 64bit here.

---

### Post by warrencon on 2012-10-27
> **puntigamer said:**
> Hi folks,
I've an older PC, and I would like to use it with Lubuntu, because it's much faster than Ubuntu or Win XP (excuse me for the comparison). The only thing that prevents me from using Lubuntu is that I can't find any application to switch the sound card!
How can I switch audio devices from Lubuntu?

Thanks in advice!

This is close to my problem, but when I bring up the alsamixer it lets me change the device, then promptly reverts back to my embeded sound device as soon as I close it. If I leave it open, the problem persists. I can play a sound file with Audacious if I set the sound card to my USB fine, or record a file with Audacity and play it back, but when I use Firefox or Chrome to visit YouTube I get no sound.

I have spent several hours chasing this solution and I'm afraid I now have several stray files lying around where I tried to edit with terminal from instructions I found in the forum, but nothing has worked so far. If I learn what needs to be done to save the changes I make in the alsamixer panel, I can always reinstall Lubuntu 12.10 to get back clean and then apply them again.

Thanks for your patience with newbies.

**edit** I tried to disable my embeded sound card in the bios, but now when I try to run alsamixes it says it's not there. Ooops.

---

