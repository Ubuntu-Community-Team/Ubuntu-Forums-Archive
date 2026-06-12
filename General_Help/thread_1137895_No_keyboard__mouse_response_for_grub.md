---
title: "No keyboard / mouse response for grub"
date: 2009-04-26
forum: General Help
---

### Post by gregconquest on 2009-04-26
I just successfully installed kubuntu on a separate partition from ubuntu, and everything went fine EXCEPT at boot, the grub screen comes up supposedly allowing me to choose to boot the ubuntu or the kubuntu partition, but **I can't select anything**. Neither keyboard nor the mouse has any effect.

After booting into kubuntu, there is no problem.

I have a similar problem with the CloneZilla stable LiveCD. There too, when I get the first screen, my keyboard has no effect. I have to let it timeout and boot further into the LiveCD before I get keyboard functionality.

Does anyone know what I can do?

Thanks,
Greg

---

### Post by gta117 on 2009-04-26
yes, try these two things first:

1) Remove the mouse and keyboard, blow any crap out behind the machine and the cords. firmly make sure they are plugged in.

2) if that does not work right away, then use a different keyboard and mouse, if that works then there is a compatibility error with your comp. Maybe removing the hardware's software and then re-installing it might be a good idea. 


call back if anything that I suggested did not work.


-gta117

---

### Post by gregconquest on 2009-04-26
Thanks for the suggestions, gta117. I have several things to add now:
1) I tried another USB keyboard -- same behavior.
2) Using other USB port -- same behavior.
3) I can select BIOS setup hitting the <DEL> key at boot, but once in the BIOS setup, the keyboard stops responding again.
4) I dug out a non-USB keyboard from the closet, and everything wotrks in all environments with this.

So, it appears that there is at least one environment out there, used by grub and CloneZilla and BIOS that has issues seeing USB keyboards. Is this a general problem, or do some mothboards have this issue? Note, though, I changed the motherboard a few months ago. I now use a Gigabyte GA-MA78GM-S2H (with AMD 64 X2 6000+) -- before was a ASUS P4P800-E Deluxe (intel) board. The ASUS board had the same problem on some boot environements, as I recall.

UPDATE: I had to add "device manager" from "Add/Remove Applications" to finally find my motherboard / system board.

Greg

---

### Post by gta117 on 2009-04-26
when all else fails, it never hurts to look for the Manuel of it, or open your computer and take a look at the motherboard. 


Also, if all your doing is swaping usb key and mouse, then that's not a complete test. It also has to be normal old fashioned ends. (unless you really do not have it.) Why? Different ports. :D

try doing this: upgrade your bios, and motherboard, or, if that does not work, or before that, roll back both of them, first doing one, and then seeing what happens.

note: make sure you also test diffrent ports for the mouse and key, INCLUDING* other usb ports. ;) 

I am not bad with hardware. Dos and terminal... now thats another thing.


Oh, while your at it, what was the models of the keys and mouses?

-gta117

---

### Post by gregconquest on 2009-04-26
I found the source of the problem. Using the PS2 keyboard, I was able to go into the BIOS settings. "USB keyboard support" and "USB mouse support" were both set to "disabled"!

I don't see why motherboards sold in the last ten years would have such a default setting, but I changed it, and now my normal USB keyboard is finally working in grub and during BIOS -- and presumably in CloneZilla, etc.

Thanks for the help, gta117. It was contemplating a BIOS upgrade that caused me to find the problem.

Greg

---

### Post by gta117 on 2009-04-26
:D Hey man, I have been on this forum for the first time tonight, been on for like 4 hours. I have been waiting for my own problem to get fixed. 


But all night, I have not really been able to help someone out directly. Glad to see I did have some use! Also glad to say that at least my 4 hours was not a total waste in my life now too. Helping someone else so they have it easier always makes things better. 



just do me a favour bro, ;) when others pick you up, pick up another. :guitar:

-gta117

---

### Post by gregconquest on 2009-04-26
Yeah, "pay it forward" :)

BTW, what is the thread you're trying to get help on?

---

### Post by gta117 on 2009-04-26
yeah, its below in bold. been having problems with make files. Originally tried to install gnomenu, by following the instructions for 1.7, ended up with glib's make file take over and messing things up. My comp is OBSESSED with the location and make file of glib, and no mater how many times I uninstall it, it will not go away! The terminal text in open office I have on the starter would be a big help for anyone trying to help me. 


tittle: 

 **Re: Ubuntu is terrible for installing... I need help :( **

-gta117

---

### Post by pr0wl3r on 2011-11-05
I realize this thread is old, but I just wanted to say thank you for pointing out the USB Keyboard settings in the BIOS. I should have thought of that, but didn't. Glad I googled!

---

