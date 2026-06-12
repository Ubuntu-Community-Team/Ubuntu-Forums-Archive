---
title: "[SOLVED] Resize NTFS"
date: 2008-12-30
forum: General Help
---

### Post by Sin@Sin-Sacrifice on 2008-12-30
So I tried gparted to resize my ntfs partition so I can make more space for a ubuntu studio install and well... look at pic 1 and 2. In the first note that there's 152 GB empty on it (sda1). So I figured on just letting winblows have about 120 GB just in case I find another game that I can't run on wine. Well.. note in screen shot 2 that it's telling me that the maximum size is 258 GB and the minimum size is 6 MB left. It will not let me resize. No matter what I do. Is there another way, maybe through the command line, that I could resize this partition?

---

### Post by dcstar on 2008-12-30
> **Sin@Sin-Sacrifice said:**
> So I tried gparted to resize my ntfs partition so I can make more space for a ubuntu studio install and well... look at pic 1 and 2. In the first note that there's 152 GB empty on it (sda1). So I figured on just letting winblows have about 120 GB just in case I find another game that I can't run on wine. Well.. note in screen shot 2 that it's telling me that the maximum size is 258 GB and the minimum size is 6 MB left. It will not let me resize. No matter what I do. Is there another way, maybe through the command line, that I could resize this partition?

Install the ntfsprogs package and then do a ntfsfix on the partition.

---

### Post by Sin@Sin-Sacrifice on 2008-12-30
This is the output of ntfsfix: ```
Killmandline:$sudo ntfsfix /dev/sda1
[sudo] password for sin:
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS partition /dev/sda1 was processed successfully.
```

And I still have the same results.... I open gparted and it says the same size limitations and I can't change any but 6 MB. Thanks for the lead anyway.

---

### Post by dcstar on 2008-12-30
> **Sin@Sin-Sacrifice said:**
> This is the output of ntfsfix: ```
Killmandline:$sudo ntfsfix /dev/sda1
[sudo] password for sin:
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS partition /dev/sda1 was processed successfully.
```

And I still have the same results.... I open gparted and it says the same size limitations and I can't change any but 6 MB.

If gparted shows an Exclamation Mark next to the partition then it has a problem with it, if it shows a Lock then you have to unmount it before doing anything to it.

Boot into Windows and see what happens.

---

### Post by Sin@Sin-Sacrifice on 2008-12-30
Just came from windows and did a whole ship load of backups. The exclamation point is there. Hmm... Does that spell a microsoft blunder again? Damnit... I'll be right back.

---

### Post by dcstar on 2008-12-30
> **Sin@Sin-Sacrifice said:**
> Just came from windows and did a whole ship load of backups. The exclamation point is there. Hmm... Does that spell a microsoft blunder again? Damnit... I'll be right back.

When you resized the partition the UUID will have been changed, you need to change your /etc/fstab file to reflect that change (do a forum search for detailed instructions).

---

### Post by Sin@Sin-Sacrifice on 2008-12-30
Yeah... I don't think I'm going to resize it. I couldn't even load my winblows recovery disks. I have a recovery partition and 2 recovery disks that I made and neither of them will boot. I can get the initial vista "splash?" but nothing more than a blinking light from the box (light for hard drive) on all 3. Seriously disappointed.... So then. Does that mean I have to buy windows again in order to reinstall it?

Post script: I was thinking hard drive problems but then would ubuntu load? Just a thought. I would think winblows would at least be able to recover by adding the new data to stable sectors. Guess winblows is that shippy...

---

### Post by Sin@Sin-Sacrifice on 2008-12-30
So I thought I'd check in on my g1 before I hit the button to install ubuntu on the whole of the drive to see if there's any objections. Here goes nothing...

---

