---
title: "performance"
date: 2009-03-23
forum: General Help
---

### Post by leedsdevil on 2009-03-23
Hey. im interested in learning how to tweek and make my older pcs run faster i have found some options around here in the forums but now since i swapped out computers i cant find them i guess im looking to learn how to switch desk top managers, turning off things that i dont use and any other ideals or suggestions.I am trying to stay with Ubuntu. i didnt like puppy and DSL was ok. i do know that if you place your swap partion to another drive will give you more performance  thanks inadvance

---

### Post by cariboo on 2009-03-23
I think you are suffering from a few misconceptions. 

Where swap is located doesn't make any difference, as it is only used when you run out of ram. During normal operation everything is run from ram, once there is no more ram to be used then swap is used.

You can turn of start up options by going to System-->Administration-->Preferences-->Sessions and turn off other services at System-->Administration-->Services.

If you are running older hardware I would suggest having a look at AntiX, it is debian based, so there isn't that much difference between it and Ubuntu. I'm running it on a PII 350Mhz Compaq with 256Mb ram, and it runs quite acceptably. The only thing I changed was installing Opera and I use it instead of FIrefox.

Jim

---

### Post by mb_webguy on 2009-03-23
If you're using a system with limited memory, then swap *will* be used fairly often, and you *would* gain a slight performance boost by putting swap on a separate drive.

The two best ways to increase the performance of older computers is to increase your memory (which is relatively cheap, especially in the amounts supported by older computers) and use lightweight alternatives to applications.

Xubuntu is better for older computers than Ubuntu because it uses a more lightweight desktop environment and applications than Ubuntu.  You can go a step further and not use a full desktop environment at all, and instead opt for a windows manager like Openbox.  I have an older desktop using Xubuntu as a base, but with Openbox and PyPanel instead of the Xfce desktop.

Here's a [list of performance guides for Ubuntu]("http://blog.lxpages.com/2007/04/24/ubuntu-performance-guides/"), but most of them are aimed at increasing performance on newer computers by doing things like decreasing swappiness or enabling concurrency during boot.

---

### Post by RedSquirrel on 2009-03-23
Install a command-line system and build up from there. Pick a light window manager, e.g., fluxbox, openbox, jwm, icewm, etc.

[http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)

---

### Post by leedsdevil on 2009-03-24
WOW wonderful ideal thanks Red! thats sort of what i was looking for and as every one else thanks for you imput. when you have an older computer that extra hard drive with the swap on it does help small gain but still a gain i have done it and you can see a difference give it a try

---

### Post by linux_tech on 2009-03-24
minimal install download
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

