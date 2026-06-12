---
title: "Mouse/Keyboard freezes on Demension E521 running feisty."
date: 2007-08-26
forum: Dell  Ubuntu Support
---

### Post by blackheart3 on 2007-08-26
When using the computer the mouse/keyboard would randomly stop working completely (mouse usually goes first).  When using multiple mice and keyboards the other mice continue to work normally until they are used and eventually "freeze" while the one being used "freezes",  with the keyboard after one freezes the subsequent one would do the same as the mice but when the key pressed at the time the other one froze is pressed it will treat it like the key is being held down until you press another button. This problem is consistent with most distros I've used on this computer, and seems to be made worse when using a dual monitor.  This problem was actually fixed for awhile, but I was changing a lot of things and do not know what fixed it specifically.  Unfortunately I have been having internet problems and during one of the 24 hour offline times I got bored and started messing with the hotkeys,  getting stuck in a black screen I was tired and really annoyed and tried to repeat the keys I pressed to get in hoping to get out, this lead to me ending up in a black screen with just my mouse pointer which after a bit froze. After which the problem has returned,  any ideas? (reinstalling doesn't work, problem persisted, probably because it was there at the start anyways)

---

### Post by mbdiego on 2007-09-04
Hi. Did you find anything that help? I got the same problems. Let me know please.

---

### Post by jb201116 on 2007-09-11
I have just installed Feisty on my Dimension E521 and have had the same problem. Firstly I am assuming that you have a similar configuration to mine being:
1GB RAM 
Geforce7300le Graphics
AMD X64 3200 Processor
Broadcom 4400 10/100 on board NIC

What I have found partially resolves the problem is to amend the boot parameters to be  -noapic apic=off


I am going to try updating the bios and all drivers from the Dell Site today, and then look at the latest NVidia drivers. (as windows is installed on the original drive and I have booted feisty onto a new 320GB drive)

I believe that part of the problem comes from the flgrx ATI drivers hence why I am going to be doing a lot of upgrading today.....:popcorn:

Oh and one thing... If anyone knows how to get the broadcom NIC card to be recognised using SOLARIS 10 I would really really appreciate it

Hope this helps...

jb201116
OpenOffice &StarOffice Guru.

---

### Post by jb201116 on 2007-09-11
> **jb201116 said:**
> I have just installed Feisty on my Dimension E521 and have had the same problem. Firstly I am assuming that you have a similar configuration to mine being:
1GB RAM 
Geforce7300le Graphics
AMD X64 3200 Processor
Broadcom 4400 10/100 on board NIC

What I have found partially resolves the problem is to amend the boot parameters to be  -noapic apic=off


I am going to try updating the bios and all drivers from the Dell Site today, and then look at the latest NVidia drivers. (as windows is installed on the original drive and I have booted feisty onto a new 320GB drive)

I believe that part of the problem comes from the flgrx ATI drivers hence why I am going to be doing a lot of upgrading today.....:popcorn:

Oh and one thing... If anyone knows how to get the broadcom NIC card to be recognised using SOLARIS 10 I would really really appreciate it

Hope this helps...

jb201116
OpenOffice &StarOffice Guru.

**UPDATE** 

By upgrading BIOS and various other drivers from the DELL support site, and having both the mouse and keyboard loaded into the first to USB ports on the back Feisty is now running without issue having added the   -noapic apic=off to the boot loader

Feisty is running with no issues and is stable. (no freezing and no graphics issues) :guitar: :-\"

jb201116
OpenOffice & StarOffice Guru

---

### Post by blackheart3 on 2007-09-27
Thanks,  everything is working fine now,  updated the bios a bit ago but forgot to update.  Thanks again.

---

