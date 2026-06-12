---
title: "XP Refuses to boot without USB Flash Drive After Ubuntu Install"
date: 2009-05-04
forum: General Help
---

### Post by Bobbert9 on 2009-05-04
Hey, I've been having trouble with my Dell Vostro 1500.

Earlier this evening, I purchased an 8GB USB Flash Drive and loaded up a 9.04 LiveCD to try to install Jaunty to it so I would have a portable Linux to load up anywhere. It worked, but now Windows XP refuses to boot without the flash drive plugged in. I get a GRUB error right after POST, I think that GRUB has overwritten the built in boot software. Is there some way to reinstall the old one for use when the USB is not in my system, or at least make a copy of GRUB on XP's HD?

I saw a topic on this subject and printed a few posts of tips, but I cannot find it a second time, and the topic was regarding Vista. Do the instructions change in the case of XP SP3?

---

### Post by delcypher on 2009-05-04
Hi unfortunetly you've gone about making a live Ubuntu USB stick the wrong way. 

Running the live cd and telling it to install to your USB stick will shorten it's life greatly (the swap partion will constantly be written to!). Also when you use the livecd to install it will have installed GRUB (a bootloader) to your hard disk instead of your USB stick. 

To prevent the live cd install doing that you need to click the advanced button at the very last stage of install. See my post [here]("http://ubuntuforums.org/showthread.php?t=1147137"). There is a [screen shot of this here.]("http://ubuntuforums.org/attachment.php?attachmentid=112243&d=1241334255")

So here's what you need to do sort it out.

1. You need to fix the boot partition. You can do this with an XP setup cd (go into recovery console and use fixmbr and fixboot). I think the method for vista is slightly different as the tools fixmbr and fixboot are not on the vista DVD, but seeing as you have XP you'll be fine. Check the link to my other post above for more information.

2. To make a proper Ubuntu USB live stick you can do it two ways (there are probably more, but I only know two). You need the ubuntu live disc image (.iso).

- Use the built in ubuntu start-up disc creator (Systems > Administration > Create USB start up disc). This method has the advantage that it'll create a persistence file so all changes you make to Ubuntu on the USB stick are saved. This only works with the ubuntu .iso files.

- Use a program called [unetbootin]("http://unetbootin.sourceforge.net/") to make it. This has the disadvantage that it has no persistence file, but it supports any bootable .iso file and not just the Ubuntu ones.

Good luck!

---

### Post by Bobbert9 on 2009-05-04
Thanks for the tips. Will doing this affect any of the saved files on my XP installation? Whatever needs to be done to Ubuntu is fine, I haven't saved any critical files to it yet.

---

