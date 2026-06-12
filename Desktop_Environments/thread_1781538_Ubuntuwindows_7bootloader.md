---
title: "Ubuntu/windows 7/bootloader"
date: 2011-06-13
forum: Desktop Environments
---

### Post by mhtsaras2 on 2011-06-13
i have a laptop with windows sev7en
i decide to put there ubuntu
when i install ubuntu there it install also ubuntu bottloader
today i decide to remove ubuntu
i delete the partitions where ubuntu was installed there
but i still have ubuntu bootloader
and it cant boot windows sev7en !!!

any ideas ??

(i have ubuntu 10.10 in bootable USB)

---

### Post by YesWeCan on 2011-06-13
Yes, this is a very common problem that people encounter.

You need to restore the original MBR on your Windows hard disk that the Ubuntu installation process re-wrote.

If you have your Windows CD you can run a fixmbr utility.

Otherwise, you can boot a Ubuntu live USB and do the following in a terminal:
[B]sudo apt-get install lilo
sudo lilo -M /dev/sda mbr[/B]

This assumes that your Windows hard disk is sda. It will be if you only have one hard disk, and probably will be even if you do not.

---

### Post by 3Miro on 2011-06-13
I think the proper way to uninstall Ubuntu is to go into Windows, repair/reinstall the windows boot-loader and only then remove the Ubuntu partitions.

You can do that again by reinstalling Ubuntu (just the minimal install to get the boot-loader). Then go into windows and do the proper procedure.

There may be a way to fix the windows boot-loader using a windows CD/USB, but I am not sure how.

---

### Post by mhtsaras2 on 2011-06-13
@YesWeCan

when i type in sudo apt-get install lilo
it writes me :

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: Problem renaming the file /var/cache/apt/pkgcache.bin.xdwgb2 to /var/cache/apt/pkgcache.bin - rename (5: Input/output error)

@3Miro
yes i could if i had the CD but it is a laptop and the data files are in the HardDrive in a  "hidden" partition ...and i can't boot up to there !!

---

### Post by YesWeCan on 2011-06-13
Yes, I vaguely recall it complains a bit. I'm not sure whether this caused the install to fail completely. Try the second command anyhow - it won't hurt anything.

Otherwise do as 3Miro suggested and reinstall Ubuntu so you can boot Windows again, then use Windows to restore the MBR, then use Windows to delete the Ubuntu partition.

OR

For convenience in the future, install Ubuntu to another disk, a USB stick for example, then you can use this as a handy means to boot your other OS's if you have a similar problem again. You just boot this Ubuntu and run sudo update-grub to add all your OS's to its boot menu.

---

### Post by mhtsaras2 on 2011-06-13
a)ubuntu@ubuntu:~$ sudo lilo -M /dev/sda mbr
   sudo: lilo: command not found
b)it finds some problem installing ubuntu again ...it fails

is the same bootloader also for other linux  distributions like fedora or backtrack??

---

