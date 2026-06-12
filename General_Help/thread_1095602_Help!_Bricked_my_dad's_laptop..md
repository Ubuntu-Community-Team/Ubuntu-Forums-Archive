---
title: "Help! Bricked my dad's laptop."
date: 2009-03-13
forum: General Help
---

### Post by QuickBrownFox on 2009-03-13
My father gave me his laptop complaining that windows xp was getting too slow so I decided to try Ubuntu Netbook Remix. Made a bootable USB key with the instructions here [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

However this apparently uses the entire drive without asking! Within 5-10 seconds of many lines of text on the screen I got the impression that this was happening so I immediately hard switched the laptop off.

So then I booted up with an ubuntu live USB and I GParted reports just 1 partition (there were previously 6 or 7) taking up the whole disk with 7GB used. It is an ntfs partition labelled "Recovery Partition".

Don't know what to do. I can only pray that my father doesn't have anything important on there and I will find out when he wakes up. Please, anyone let me know how I can undo this if possible (I suspect the damage has already been done). Also, if anyone can get the page linked above changed to have a big fat warning that this will wipe your disk then they should do it now!

---

### Post by taurus on 2009-03-13
See if TestDisk can recovery files on the "old" ntfs partition.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by KayakJim on 2009-03-13
The recovery partition is most likely a snapshot of the drive the way it was when it shipped from the factory when the system was purchased instead of being a backup of the drive prior to this event.

---

### Post by QuickBrownFox on 2009-03-13
> **KayakJim said:**
> The recovery partition is most likely a snapshot of the drive the way it was when it shipped from the factory when the system was purchased instead of being a backup of the drive prior to this event.

I suspected as much. I'm not hopeful. Trying testdisk soon.

---

### Post by D.Gelman on 2009-03-14
First: Don't Panic. Chances are, if you panic you will cause damage that hasn't yet occured. Your goal should be first to capture what is left on the drive, before you destroy it while you're trying to save it.

Its unlikely that your Ubuntu install deleted any data without your express permission. Chances are that you have just screwed up the boot process somehow, so the computer is no longer able to find the Windows system.

Please provide more details about the Windows version (XP, Vista, etc). Also, the output from `sudo fdisk -l` would be helpful.

If I were in your position, I would first create a backup of the complete drive, using a utility like partimage -- which is part of the SystemRescueCd (sysresccd.org) -- to prevent myself from destroying data I didn't know existed. Then you can go ahead and try to whatever other methods with the security of being able to go back to your initial state.

Next time you do this, I suggest making the backups first -- the partimage/sysresccd solution is a great way to wipe the slate clean after you've made some big mistakes.

---

### Post by QuickBrownFox on 2009-03-14
Thanks very much everyone for your helpful replies. I used testdisk to rebuild the partition table and then reinstalled grub. Then windows would boot but it was very, very, very slow and would not log in. Using a juanty alpha live CD (it was handy) I able to recover the important data (which wasn't that important anyway, I was told) and then used the manufacturer's system recovery disc to format and reinstall windows. Then I installed Linux Mint and it's working very nicely as a dual boot system.

Thanks again for the help. Ubuntu community wins.

---

