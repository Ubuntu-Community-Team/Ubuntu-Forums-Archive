---
title: "need some help with hard discs handling"
date: 2005-10-26
forum: Desktop Environments
---

### Post by mxyzptlk on 2005-10-26
i have two hard discs installed in my pc, one with ubuntu and the other with xp.

when i installed ubuntu, the app called GRUB made the booting section so i can choose between Ubuntu and XP.

but i wanted to make the Ubuntu disk the primary and the XP disk the slave, so i changed phisically the BIOS config and the disks jumpers.

BUT EVERYTHING WENT DOWN

and i just couldnt get in to any system and GRUB failed,

any suggestion?

is it possible to install only the GRUB with the new hardware configuration?
is it possible to access to windows files trought Linux:confused:

---

### Post by KingBahamut on 2005-10-26
The best thing to do is to change back the hardware configurations. Im uncertain why making one primary over the other would do much for you. 

But, alternately you could probably because you installed grub on your primary MBR. What you could do is grab a live cd , boot it, and attempt to repair grub that way.

---

### Post by metoo on 2005-10-26
May be you can get it up this way:

In the BIOS change to boot from the 2nd harddisk first. This should give you grub. But all entries in grub are now reversed. They are taken from /boot/grub/menu.lst

Luckily, at boot in grub you can edit the lines before booting. Hit e on the linux entry and select the lines mentioning /dev/hdb or /dev/sdb, which are now /dev/hda or /dev/sda . Hit e on them and change them. To make this permanent, change the entries in /boot/grub/menu.lst Apparently mentioning of hd in the linux section should now be hd(0,0) .

But every kernel upgrade with a re-run of grub will revert this back until you re-installed grub properly to the (now) first hard disk.
Then the boot partition on the ubuntu hd must be marked as bootable (cfdisk can tell you that) and in the BIOS you would switch back to boot from the 1st hd 1st.

Windows is tricky. It might be possible/required to add some magic hd-swap lines to the grub menu to fool the windows boot loader. But this is beyond me. (had this once in the past)

If there is no real need, just listen to the previous poster and revert the hds back.

Windows files:
On FAT32 (vfat in linux) you can read and write.
NTFS you can read without problems. Writing requires some tools which use windows dlls. This is more difficult to achieve, but should be possible.

---

