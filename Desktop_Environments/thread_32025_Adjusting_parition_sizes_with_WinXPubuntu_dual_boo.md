---
title: "Adjusting parition sizes with WinXP/ubuntu dual boot"
date: 2005-05-05
forum: Desktop Environments
---

### Post by Rehevkor on 2005-05-05
I've decided that Windows is only worth 8gb of my Dell laptop's hard drive, and Ubuntu is worth the remaining 32gb ( ;-) ) so I used gparted to delete the WinXP ntfs partition and created a new ext3 partition from it, leaving 8gb unallocated.

I then popped in my WinXP to reinstall it to the 8gb partition... and smacked myself in the forehead. I already have 4 partitions! The Dell utility partition, linux root and swap, and the new ext3 partition. Thus, Windows won't let me create a new partition on the unallocated space.

I could just delete the Dell utility partition, but I intend to sell the laptop this fall and get a new one. I figure I should leave that there in case the next user needs it for the diagnostic tools.

I also don't want to get into any crazy partitioning to make it work, since I would hate to accidentally blow away my Ubuntu install. I've spent a LOT of time tweaking it, and I would hate to have to do it all over again.

Ideally, I would like to merge the newly created 22gb ext3 partition with my current root partition (also ext3). If this simply can't be done, I'm open to suggestions.

Btw, ubuntu rocks :grin:

P.S.
I forgot to mention I do have a fallback if this approach doesn't work. I *think* I do, anyway.

Before I started all this, I used Norton Ghost in WinXP to create a backup image of the linux root partition and copied it across the network to my desktop. If all else fails, I could possibly remove the current linux root partition, install WindowsXP on the 8gb partition, then use Ghost to restore the linux root partition to the remaining space on the drive. Theoretically, this would result in Windows on the 8gb partition, ubuntu on 31gb of the remaining space, and the 1gb swap partition.

Would this work, or am I totally insane? :)

---

### Post by Xian on 2005-05-05
I've not had a need to use it, but I recall that the Ubuntu Install-CD partitioner has a copy partition function that might be of use to you in this situation. You could just copy over your root directory to the new ext3 partition, then use that as root and install Windows on what used to be root. Just keep the old directory files there until you can boot from your new root.

If that doesn't work then you could just mount the new ext3 partition and copy over in a terminal session your current root directory to that location. You'd have to edit your fstab and menu.lst files and perhaps reinstall grub to boot from that portion of the HD, but that should also be doable.

---

### Post by Rehevkor on 2005-05-05
[QUOTE=Xian]I've not had a need to use it, but I recall that the Ubuntu Install-CD partitioner has a copy partition function that might be of use to you in this situation. You could just copy over your root directory to the new ext3 partition, then use that as root and install Windows on what used to be root. Just keep the old directory files there until you can boot from your new root.

If that doesn't work then you could just mount the new ext3 partition and copy over in a terminal session your current root directory to that location. You'd have to edit your fstab and menu.lst files and perhaps reinstall grub to boot from that portion of the HD, but that should also be doable.[/QUOTE]
 Maybe, but my current root is 5gb. I wanted to roll that into the new ext3 partition. I already have 8gb of unallocated space set aside for Windows.

---

### Post by Xian on 2005-05-05
[QUOTE=Rehevkor]I then popped in my WinXP to reinstall it to the 8gb partition... and smacked myself in the forehead. I already have 4 partitions! The Dell utility partition, linux root and swap, and the new ext3 partition. Thus, Windows won't let me create a new partition on the unallocated space.[/QUOTE]
You are going to have to move one of those three partitions to a logical drive so that Windows will have a primary partition to install into. I would imagine that your utility and swap are not large enough, so that just leaves the root directory. Change the new ext3 file system into an extended partition, and then create whatever size directory you would like for Ubuntu from that reserve. Copy over your root path and then format the former root partition as either FAT or NTFS. The XP install will take back over your MBR so you'll need to have to plan on reinstalling grub and making Ubuntu bootable once again.

---

### Post by GTvulse on 2005-05-05
You could remove the swap partition and recreate it as a *logical* one. Do make sure that both Windows and Ubuntu's root are in primary partitions. Well... Windows and the partion where you want to install grub. Neither will boot up from a logical partition.

---

### Post by Xian on 2005-05-05
[QUOTE=Rehevkor]Maybe, but my current root is 5gb. I wanted to roll that into the new ext3 partition. I already have 8gb of unallocated space set aside for Windows.[/QUOTE]
You can roll that into the new ext3 partition without a problem. The issue is in how to create a primary partition for XP to install into and still keep your current data intact. You can't use the current root since it is too small, and I will assume the other partitions (utility and swap) are even less adequate in space. Then only thing I can suggest is to ditch the ext3 partition for right now and make everything unallocated that is not in the utility, root, or swap directories. So you would have something like:

hda1   utility
hda2   root
hda3   swap
unallocated -- remainder of HD

Then you could delete the swap partition and feed it into the unallocated space. This would just leave you with the utility and root paths, and the rest of the HD as unallocated. Now create two more partitions: one for the XP installation and one as an extended partition. And then finally create another two partitions for your new root and swap from that extended space. So, now you would have this:

hda1 utility
hda2 root
hda3 NTFS
hda4 EXT
hda5 new root
hda6 swap

Copy over hda2 to hda5 and now you've populated your new root directory. This should have you completely setup except that you have a hda2 partition with unused space of 5GB. But, you could easily peel off one of your system paths from hda5 and use that to enhance your root partition. For example, you could place your /home directory on hda2 and that would free up more room on hda5. Or, you could peel of another path like /usr, /var, and so forth.

---

### Post by Xian on 2005-05-05
[QUOTE=Rehevkor]Maybe, but my current root is 5gb. I wanted to roll that into the new ext3 partition. I already have 8gb of unallocated space set aside for Windows.[/QUOTE]
You can roll that into the new ext3 partition without a problem. The issue is in how to create a primary partition for XP to install into and still keep your current data intact. You basically have to get this kind of setup:

hda1 utility (if this is necessary)
hda2 XP
hda3 root
hda4 EXT (extended)
hda4 swap

---

### Post by Rehevkor on 2005-05-05
[QUOTE=Xian]You can roll that into the new ext3 partition without a problem. The issue is in how to create a primary partition for XP to install into and still keep your current data intact. You basically have to get this kind of setup:

hda1 utility (if this is necessary)
hda2 XP
hda3 root
hda4 EXT (extended)
hda4 swap[/QUOTE]
 Ok. Now how can I actually merge the new ext3 partition into the root partition? I'm relatively new to working with linux partitions, so I have no idea :)

---

### Post by momo66 on 2005-05-05
qtparted will do the trick

---

### Post by Rehevkor on 2005-05-06
[QUOTE=momo66]qtparted will do the trick[/QUOTE]
 I loaded up my Knoppix live cd and tried it, but only the Property, Format, and Delete options were available for the ext3 partitions. I had unmounted the partitions before starting qparted, and I checked again to make sure. How exactly can I do this?

---

### Post by Rehevkor on 2005-05-07
Well? How can I merge that ext3 partition into the root partition without destroying the data on it? I can't find a solution anywhere.

---

