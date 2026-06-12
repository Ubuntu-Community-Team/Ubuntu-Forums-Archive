---
title: "Creating a Windows partition"
date: 2006-06-22
forum: Desktop Environments
---

### Post by L2wis on 2006-06-22
Hey guys before anyone states i know the easiest way round the windows and linux duel boot is windows installation then the linux but...

I've had ubuntu as sole os for a month or so now but miss battlefield 2 too much and want to have windows purely for BF2 and keep linux for everything else.

My question is this: How do i create a windows partition on my fully formatted linux HDD? I've looked in Gparted for any easy options but it didn't seem like it would be able to resize etc.

If anyone could post some instructions i'd greatly apprechiate it :D

Regards

Lewis

---

### Post by Blind-Summit on 2006-06-22
gparted won't let you resize at all? I can only think that you need to find some package to let you shrink down the main partition and create some empty space for windows. Search the package manager for "partition" and see what comes up. One of them must be able to help you out.

Other than that - you may try making a ghost image of your linux setup, then setup your partitions again, install windows and then restore the linux image to the other partition. Just make sure to leave enough space for it to restore.

I've made images and restored them just fine - but it may be worth making a couple just to be safe.

Having said that - you need to create the partitions on a different partition to the one you are imaging. I don't know if your swap partition is big enough.

hmm - go with finding a better partition resizer first

---

### Post by queenorych on 2006-06-22
Gparted should resize the ext3 partition.  You must boot off the live cd, then resize the partition.  Also look into codega, it allows you to play a lot of windows games right in the safety of ubuntu.  It even runs some faster than on windows.

---

### Post by L2wis on 2006-06-22
[QUOTE=queenorych]Gparted should resize the ext3 partition.  You must boot off the live cd, then resize the partition.  Also look into codega, it allows you to play a lot of windows games right in the safety of ubuntu.  It even runs some faster than on windows.[/QUOTE]

How come you have to boot off the live CD to resize the partitions? Sounds odd cos when i was running the live version u can't save files and stuff?

When reinstalling Windows will it setup a boot file to choose between xp and ubuntu? 

I'm not to intrested in any emulator software unless some1 knows of a complete guide to getting bf2 working on the latest patch online.. I've not found one and ive searched tonnes.

Regards and thxs for the help so far.

---

### Post by Buffalo Soldier on 2006-06-22
I think you have to use the liveCD because if you boot into the Ubuntu on your harddisk, Gparted can't resize the partition. Because Gparted needs the partition to be unmounted. And I don't think you can unmount your / or root partition when you're still on it.

---

### Post by L2wis on 2006-06-22
[QUOTE=Buffalo Soldier]I think you have to use the liveCD because if you boot into the Ubuntu on your harddisk, Gparted can't resize the partition. Because Gparted needs the partition to be unmounted. And I don't think you can unmount your / or root partition when you're still on it.[/QUOTE]

Ah okay cool, it's been a little while since i last used the live CD, i just put it in and booted from it (i think) i logged in and tried to fiddle with the partitions again but move/resize is still blanked out. and when i click unmount it just says it's busy.

It seems like it booted from HDD again, but im sure it said booting from CD in the BIOS loading screen.

---

