---
title: "Need help: to boot Wubi-Ubuntu installed on HDD from a bootable CD"
date: 2009-04-23
forum: General Help
---

### Post by Xanf on 2009-04-23
I need help to get working the following non-standard WUBI / ubuntu installation on my VISTA laptop with drive C: formatted to NTFS:

1. I don't have administration rights on this laptop to instal any applications.
2. But I'm allowed to create any new folders on the laptop's drive C: and put any files in these folders
3. I'm not allowed to add any files in the root directory of drive C:
4. I'm not allowed to modify any files in the root directory of drive C:
5. My laptop can boot only from either HDD or from INTERNAL CD drive. Booting from any USB devices is not allowed and disabled in BIOS.
6. On drive D: (also NTFS) of the laptop I may store any files and folders as I like - it's a "user data drive"

I need to have the persistent files that are created during the wubi installation of UBUNTU within Windows to be stored in some directory on my NTFS drive C: - and to create a bootable CD that will only start booting - and then take the files on the hard drive and continue normal boot from it to the normal persistent installation of "ubuntu within wubi".

To achieve that I did already the following steps:

1. On another laptop I replicated the above mentioned restrictions.
2. I installed ubuntu with wubi on the another PC - then simply copied the folder "ubuntu" with all its subfolders and files from this PC to the "development" laptop.
3. I moved the "wubildr.mbr" to the folder "ubuntu" and "wubildr" file to the drive D: - so on the drive C: there is no new (unexpected for any administrator) files in the root directory.
4. Now, if I change the boot.ini file on drive C: to have the option for loading the C:\ubuntu\wubildr.mbr - my ubuntu linux works fine.

But from this step onward I need to return the boot.ini on drive C: to its original state - and make use of this "wubilized" ubuntu installation from a bootable CD.

(well, in reality, I also renamed the folder "ubuntu" to some other, non-attracting name as "temp", removed all the unnecessary files from there, modified the menu.lst of the grub4dos and the menu.lst of the /boot/grub/ to the real paths  as "c:\temp\disks\", etc. And this all works OK with modified boot.ini. So tha last thing I need to do - is to get rid of the necessity to use the boot.ini from the C: - and initiate booting from a CD).


I have found the older thread re wubi on the USB stick to boot and use the persistent ubuntu image files stored on the hard disk: [http://ubuntuforums.org/showthread.php?t=946356](http://ubuntuforums.org/showthread.php?t=946356)

But even using the ideas from there I'm not able to build such a boot CD that I need, unfortunately.

Does someone have some ideas on how to do that?

---

### Post by Xanf on 2009-04-24
???

---

### Post by Xanf on 2009-04-27
If this is still needed to anyone else - I've finally made it. It was so simple that this was why I didn't realized it from the beginning how I should do it.

So - a short HOW TO:
Prerequisites: we do have some linux (say ubuntu in our case) installed with wubi on a windows partition - or maybe even simply copied from another PC.

To boot it from a bootable CD without modifying the windows boot.ini file - and actually without a need to have the wubi.exe and the whole wubi related stuff (as wubi menu.lst and .mbr file) on the HDD -  we do the following:

1. create a directory, say iso_root in your current folder (say in your user directory if you are in linux now)
2. copy to this iso_root folder the file wubildr - and rename it to grldr. This may be not needed, but this is what I did while playing with grub before - so I simply leave it here as a suggestion.
3. create a text file named menu.lst in the iso_root folder  - and put there the menu options for the loader to find the grub location in your ubuntu (or other linux) directory - something similar to what I did below:

```

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /recovery/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /recovery/disks/boot/grub/menu.lst
	configfile /recovery/disks/boot/grub/menu.lst

title find /recovery/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /recovery/install/boot/grub/menu.lst
	configfile /recovery/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

```
4. now we create the iso image out of this:
```
mkisofs -R -b grldr -no-emul-boot -boot-load-size 4 -o my_magic_boot_cd.iso iso_root
```
note: if you don't rename wubildr to grldr - use wubildr in the command above instead of grldr

5. now we burn the resulting iso image to a CD - and can try it working.

After it's checked and working successfully - we don't need anymore the directory WINBOOT in the original "ubuntu" folder - we can delete it. As well as all the instances of the wubildr, wubi.exe, wibildr.mbr - if they are still residing somewhere on your hard disk - i.e. in the root of C: drive - we can delete too. And now we don't need the record for the wubi loader in the boot.ini file as well.

As a result - we've got an ubuntu installed on a windows partition ( in my case residing in the folder of a non-attravtion name) and having no signs that it's a working linux installation. Without our self-made CD nobody without a good knowledge of linux and wubi will be able to boot it. To every average windows administrator this looks only as a bunch of useless files stored on the disk - which we can always explain as a backup copy of the data files say from your external drive, etc. And, yes, sorry I put them to the drice C: - but there is no violation of the rule forbidding installation of any software in your windows and no overriding of the missing local adming rights in it too. :-)

---

