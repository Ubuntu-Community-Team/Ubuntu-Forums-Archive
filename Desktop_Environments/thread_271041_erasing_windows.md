---
title: "erasing windows"
date: 2006-10-04
forum: Desktop Environments
---

### Post by heffo_j on 2006-10-04
Hi all,

I want to erase my XP partition but I am worried about breaking my startup. Can someone either tell me how to do this without damaging start up or point me to a site that gives a simple and clear instructions on what to do. 

I am happy to reformat the partition as either ext3 or even FAT32. 


Regards
John

---

### Post by wieman01 on 2006-10-04
Best would be if you uploaded a screenshot of your partitions (GParted if possible). Second best option is to run this command & post the output:
> sudo fdisk -l
To make it a bit easier for us perhaps make the effort to upload an image of GParted. :-) The rest should not be much of a deal...

---

### Post by heffo_j on 2006-10-04
Snap shot of Gparted:

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=16868&stc=1&d=1159958935[/IMG]

What do you make of it?

Regards
John

---

### Post by rogier.de.groot on 2006-10-04
Just unmount the windows partition (if it's mounted), throw it out of /etc/fstab (if it's in there) and mkfs /dev/hda1. I see no reason to make it FAT32 so stick with ext3. Add an entry in /etc/fstab to automount it (or modify the windows line if it's allready in there). Even if this screws up your startup (which shouldn't happen) you can always reinstall grub from the livecd - with sudo grub install /dev/hda or some such (look up the man page if you're having trouble).

---

### Post by wieman01 on 2006-10-04
Unless you want to move **hda2** and merge it with **hda1** it's as simple as Rogier has explained. However, if you want to move **hda2** to where **hda1** is right now, it'll be slightly more complicated but also manageable.

Once you have erased your Windows partition, you will have to delete the boot loader entry for Windows from your GRUB config file. Open the file with "gedit" and search for WinXP, then delete it:
> sudo gedit /boot/grub/menu.lst

---

### Post by rogier.de.groot on 2006-10-04
Hmm... darn, I forgot all about erasing the boot entry! Silly me... Anyway, how do you make hda1 & hda2 into one big partition with the linux install from hda2 on it? I'd really like to know in case I ever decide to nuke the win2k install on my dual-boot setup... Which will happen as soon as Kubuntu doesn't crash randomly anymore and amarok starts playing MP3s when I click on them... At any rate, sorry for overlooking such an obvious step!

---

### Post by wieman01 on 2006-10-04
Nah... Don't worry. It's an obvious step but does not really make a difference. It's merely cosmetic. :-)

Moving hda2 to hda1 will be a bit tricky because you see...

>> used space of hda2 > size of hda1. 

But it's possible to do that. The process would look something like this (in this case):

1. Boot from Live CD.
2. Fire up GParted.
3. Resize hda2 so that you free up space right of it.
4. Create a new partition: hda4
5. Format hda1: ext3
6. Move the home folder from hda2 to hda4 (copy/move - command line).
7. Move remaining file system (root) from hda2 to hda1 (command line).
8. GParted: Delete hda2
9. Resize hda1 and merge it with hda2.
10. Command line: Copy home folder from hda4 to hda1.
11. GParted: Delete hda4
12. Resize hda1 and merge it with hda4
13. Run GRUB configuration tool from command line.
14. Update /etc/fstab.
15. Reboot & enjoy.

It's better if we looked at your system, however, first and then decide what needs to be done. But the steps are the same:

1. GParted from Live CD.
2. GRUB config tool.
3. GRUB config file "/boot/grub/menu.lst".
4. /etc/fstab.

---

