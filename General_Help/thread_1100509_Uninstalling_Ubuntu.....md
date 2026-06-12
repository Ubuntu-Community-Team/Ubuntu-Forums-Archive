---
title: "Uninstalling Ubuntu...."
date: 2009-03-19
forum: General Help
---

### Post by Captain Camaro on 2009-03-19
So I am in the process of uninstalling Ubuntu from my computer and I have a few questions.

I am using the BootItng program and in the screen with all the partitions, I have no idea what is what.  I have my instructions here that say to delete all partitions except my original windows partition, but I can't figure out which one that is.

When I did my original install, I dual loaded ubuntu with xp and alloted 35 Gigs for each OS on my HD.  I've written below what is in the partition list for the program.

MBR Entry 0  Partition   6150 MB  Compaq Config
MBR Entry 1  Partition  35017 MB  HPFS/NTFS
MBR Entry 2  Partition  35150 MB  Extended
unnamed      Volume     33660 MB  Linux Native
unnamed      Volume      1490 MB  Linux Swap/Solaris

Any help would be greatly appreciated!  I really have no clue what is what in this menu...

Thanks folks,
Jared Allen

---

### Post by taurus on 2009-03-19
From that output, you can delete those two logical partitions under the extended partition.

And if you installed GRUB to menu to boot both Ubuntu and windows, you will get an error message from GRUB after you delete Ubuntu.  Therefore, you need to boot your machine with either windows disc to fix the MBR or use Super GRUB Disk, [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html).

---

### Post by Captain Camaro on 2009-03-19
Well, apparently this program has the ability to fix the MBR booting problem as well per the 'instructions' I got [here]("http://ubuntuforums.org/showthread.php?t=113630"). (Read:nonsense) :)

So, hopefully that will work.  But in review, the bottom two are the ones I  should delete.  And then, I'm assuming after I resize my Windows Partition, the "extended" mbr won't exist anymore, right?

Thanks a lot for the quick reply!

Jared Allen

---

### Post by Captain Camaro on 2009-03-19
Please guys just a little more help and I'll be out of your hair forever!  I just want to know what I'm doing before I do it :P

Thanks folks,
Jared Allen

---

### Post by Captain Camaro on 2009-03-19
So I am very inexperienced when it comes to computers... This was very hard for me, but I am learning to study what I want to do a lot before I do it.  I mess up less and I learn more.

I have discovered these two pages which greatly aide the poor instructions that I linked previously.  Perhaps a direct link to the BootItng program should be added to an Ubuntu FAQ on uninstalling, along with the link to these two pages:

[Help #1]("http://www.everyjoe.com/newlinuxuser/explanation-what-is-a-bootloader-and-an-mbr/")
[Help #2]("http://www.terabyteunlimited.com/kb/article.php?id=311")

This is just for anyone who happens upon here and needs the same help I did.

Thanks again for all your help folks and maybe I'll see you again soon.

Jared Allen

---

