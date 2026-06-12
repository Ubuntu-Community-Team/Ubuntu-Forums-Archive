---
title: "Fatal modprobe &amp; softreset failed errors on boot"
date: 2009-05-09
forum: General Help
---

### Post by alanwalterthomas on 2009-05-09
I get this message during bootup since I upgraded to 9.04, but I so far I can't be sure it's responsible for any problems. It also delays startup by ~5 seconds.
Problems I have had are:

(solved) (ext4?) filesystem problems
[http://ubuntuforums.org/showthread.php?t=1150032](http://ubuntuforums.org/showthread.php?t=1150032)
My 5 in one card reader doesn't work right.
[http://ubuntuforums.org/showthread.php?p=7245538#post7245538](http://ubuntuforums.org/showthread.php?p=7245538#post7245538)

This appears at grub boots from the hdd:

Starting up ...
[      1.948018] ata1: softreset failed (device not re ady)
[      2.048018] ata3: softreset failed (device not ready)
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory

An attached USB drive causes the modprobe line to appear twice. I'm not sure if the softreset lines are related to the modprobe one, but I'd like to 

Can anyone tell me what's going on here or how to fix it? Is there a modules.dep files that I can download & copy to that location? Thanks

---

### Post by alanwalterthomas on 2009-05-12
I opened /lib/modules/2.6.28-11-generic/ immediately after booting & modules.dep was there. I had a filesystem problem shortly after installing & I had to e2fsck -b from the live cd to get my hard drive back & it corrected several hundred values. Is it likely that's related?
Thanks for any help, I'd really like to know what's causing this. The file is there, no problem on other computers, what gives?

---

### Post by dbuttera187 on 2009-05-12
i get a softreset error too when i boot, but not the modprobe. I think the softreset has to do with a BIOS setting of a drive, such as a floppy, that is enabled but not installed. The softreset error doesn't stop me from booting or anything it just comes up everytime. As for the modprobe, all i know about that is that i used it when configuring drivers so that might have something to do with it?.

---

### Post by alanwalterthomas on 2009-05-15
bump
Help
Let me know if there's any more information I could provide that might fix either one of these errors.

---

### Post by khamil8686 on 2009-05-18
i also have this problem. maybe it is related to the problem where a clean install of ubuntu 9.04 allows me to suspend once and then when i resume gnome-power-manager tells me it is unable to get data... and then im unable to go back into suspend? i use the power button on my computer, i have it set to suspend, i get the same when i click the 'start' (unsure what to call it, windows equivalent i guess) button that has my name on it and go down to suspend. i can also click this plug icon and it gives me options to suspend or hibernate, when i click those it says suspend forbidden, not sure what it says for hibernate because i dont need hibernate and wasnt sure if it was necessary to troubleshoot the problem. i cant find a fix for this problem unfortunately after lots of googling. *pats his stack of books on linux/ubuntu* time to get reading and hopefully i figure out a solution :) i was thinking this problem was related to the gnome-power-manager thing because maybe it cant load the module when resuming because it never loaded the module in the first place when i first started the computer? anyways, no idea, im sorry, wish i was posting a solution, but im just seconding this problem ._.

---

### Post by khamil8686 on 2009-05-22
to get rid of the fatal modprobe i wrote something up that might help out :) [http://ubuntuforums.org/showthread.php?t=1162619](http://ubuntuforums.org/showthread.php?t=1162619)

---

