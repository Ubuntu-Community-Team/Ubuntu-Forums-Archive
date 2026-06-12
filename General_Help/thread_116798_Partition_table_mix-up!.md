---
title: "Partition table mix-up!"
date: 2006-01-13
forum: General Help
---

### Post by mattbarlow on 2006-01-13
Hi 
When I first installed Ubuntu 5.10 Breezy it was installed in /dev/hda7 and there was an unformatted free space just before that partition.
Now I want to format that free space and use it for data.
When I run cfdisk   it gives:

    hda1        Boot        Primary   W95 FAT32 (LBA)                  21476.21
    hda2                     Primary   W95 FAT32 (LBA)                  85904.83
    hda5                     Logical   Linux ReiserFS   [/]             20003.89
    hda6                     Logical   Linux swap / Solaris               699.15
                               Logical   Free Space                       51959.10
    hda7                    Logical   Linux ReiserFS   [/]             20003.8

After the creation of the new partition in the free space cfdisk gives:

    hda1        Boot        Primary   W95 FAT32 (LBA)                  21476.21
    hda2                    Primary   W95 FAT32 (LBA)                  85904.83
    hda5                    Logical   Linux ReiserFS   [/]             20003.89
    hda6                    Logical   Linux swap / Solaris               699.15
    hda7                    Logical   Linux                            51959.10
    hda8                    Logical   Linux ReiserFS   [/]             20003.8  

So [/] is now on /dev/hda8...
I know how to fix fstab and menu.lst but I also know from a friend of mine who has had his partition table changed, that every time a new kernel is installed by ubuntu update, menu.lst will be switched back because the system "thinks" that my root partition is /dev/hda7.

How can "inform" my system that my root partition is now /dev/hda8?

---

### Post by GTvulse on 2006-01-14
> How can "inform" my system that my root partition is now /dev/hda8?

You shouldn't have problems, as far as your stroy goes, your friend did something unusual and that borked his/her system; nothing to do with your present situation.

What you do need to do is to reinstall grub to wherever you did in the first place. The best way to do this is to run the Install CD in rescue mode, mount your primary root partition and run grub-install pointing the place where your have installed grub.

Say, you installed to the MBR, then you run the CD in rescue mode, mount your booting partition (hda5, aka (hd0,4)? I'm guessing here) and reinstall the grub stage files with "grub-install /dev/hda" or "grub-install '(hd0)'" without the double quote-marks.

EDIT: Let us know how it goes.

---

