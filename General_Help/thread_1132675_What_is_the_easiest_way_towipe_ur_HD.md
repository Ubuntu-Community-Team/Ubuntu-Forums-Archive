---
title: "What is the easiest way towipe ur HD"
date: 2009-04-22
forum: General Help
---

### Post by Bearded-flower on 2009-04-22
I want to nuke my hard drive and install jaunty, whats the easist and/or safest way to do this

---

### Post by lisati on 2009-04-22
A couple of ways come to mind. The easiest is probably to tell the installer's partitioner to use the entire disk.

---

### Post by Bearded-flower on 2009-04-22
Ok is there any other ways?

---

### Post by scheuri on 2009-04-22
Frankly I do not see any reason to wipe a hard disk if you install a new OS on it.

Usually the installer (in this case the ubuntu installer) will ask you what to do. You could go on saying to delete all recognized partitions and then make new partitions for ubuntu.
That is about it.

If you want to delete the data prior to that to present a complete empty disk (which is not necessary) to the installer...then you might want to use wipe tools usually available as isos or floppy disk image (see google).

Cheers
scheuri

---

### Post by Lunx on 2009-04-22
> **Bearded-flower said:**
> I want to nuke my hard drive and install jaunty, whats the easist and/or safest way to do this

Easiest and safest way is to do as lisati suggests. Another (fairly) simple way is to use the manual option on the installer. It will show you the partions on your drive which you can then delete and this will give you an entire free disk. You then click on that free disk entry in the GUI and select "new", this will let you create a partion of whatever size you wish for your Ubuntu installation. You need to set the mount point to **/ **and set your file system to ext3 (or ext4 if you like if you are installing Jaunty

Next you will need to create a swap area that's around 1.5 times the size of your RAM, so for 1GB of RAM you could make the swap area around 1.5GB.

Then you can select the remaining space on your drive and set it up with** /home** as the mount point. This is a good way to go about it as you can uninstall/reinstall your system without trashing your** /home** directory. 

The above is the method I have used several times now and never had a drama, it "just works". I have noticed that when I've used the guided option and then played with my partions that the swap area shown as being last, but I'm not sure it matters as it works fine for me with it set between  **/ **and **/home**

I worked this out from trial and error myself and have never been shown how to do it, so take what I've said with a grain of salt and confirm this with others first, as I would hate to have given you the wrong advice (hopefully someone else will point out anything wrong with my method, or perhaps suggest better/proper ways of doing it).

---

### Post by Sef on 2009-04-22
> Next you will need to create a swap area that's around 1.5 times the size of your RAM, so for 1GB of RAM you could make the swap area around 1.5GB.

That is not true any more.  For one gigabyte ram, I would make a one gigabyte swap.

---

### Post by Bearded-flower on 2009-04-22
Wait this how my hard drive is set out would this afect it or wouldnt it really matter?



1. In that case just mount the image to a virtual drive using Daemon Tools, Access it and run setup.exe. then continue from step #4.
2. Yes, Debian installer does not harm the MBR. just Remember not to touch sda1 & sda2 during the installation.
3. sda3 partition=Windows Local Disc (D:), Yes, WIND have it created by default. Right click 'My Computer' > Manage > Disk management,
And you'll see 3 partitions:
Windows.............................................................Linux.........
1. Hidden Recovery 3.91GB FAT32.......................sda1
2. Os_Install(Windows) (C:) 39.08GB NTFS..........sda2
3. Local Disk(D:) ~120GB NTFS...........................sda3



So because of that will i have to wipe my hard drive and THEN install or wouldnt it matter

---

### Post by Jimmynemo2 on 2009-04-22
If you are fully wiping the drive when installing the new ubuntu, what you currently have on there wont matter, just choose guided partitioning during install and it will do the magic for you.

---

### Post by lisati on 2009-04-22
I see there's a hidden recovery "disk" mentioned.
This is just my personal preference, but it might be a good idea to leave it well alone, or make a copy of it onto DVD, "just in case". The copy of Vista that came with one of my laptops came with a program preinstalled that let me make a bootable recovery DVD from the recovery partition. This was just a precaution in case I need to restore my system to an "out of the box" state for some reason (e.g. if it needs to go in for servicing)

---

### Post by Bearded-flower on 2009-04-22
Yeah but my harddrive is set out like this

1. In that case just mount the image to a virtual drive using Daemon Tools, Access it and run setup.exe. then continue from step #4.
2. Yes, Debian installer does not harm the MBR. just Remember not to touch sda1 & sda2 during the installation.
3. sda3 partition=Windows Local Disc (D:), Yes, WIND have it created by default. Right click 'My Computer' > Manage > Disk management,
And you'll see 3 partitions:
Windows.............................................................Linux.........
1. Hidden Recovery 3.91GB FAT32.......................sda1
2. Os_Install(Windows) (C:) 39.08GB NTFS..........sda2
3. Local Disk(D:) ~120GB NTFS...........................sda3


Not one partition but a few so i have to wipe it nd then install ubuntu.
so can i wipe my computer so it has no operating system what so ever so windows no ubntu no ANYTHING!
and then install ubuntu of  USB
is that possible it dosent need some sort of operting system installed to be able to turn the power on ect?

---

### Post by lisati on 2009-04-22
> **Bearded-flower said:**
> 
is that possible it dosent need some sort of operting system installed to be able to turn the power on ect?

[LIST]
[*]You'll need an operating system of some sort on USB, CD or hard disk if you want to use your computer - you won't be able to do much without one!
[*]Putting a copy of the recovery partition on DVD is so you have something to work with if something goes wrong. If you are happy with the possibility of not getting windows back at all, then don't bother worrying too much.
[/LIST]

EDIT: As long as you have a bootable installation CD or USB it won't matter if you wipe your hard disk. It is always a good idea to make a copy of important data "somewhere else" (i.e. not on the main hard disk), just in case something goes wrong. This includes any recovery partition your computer might have.

---

### Post by Bearded-flower on 2009-04-22
Yeah thanks isati but i found out you can do all that through ubuntu without having to wipe the HD
and i have got a copy of the XP back up disk so if hell freezes over and i need windows ill have that.
and windows 7 isnt to far away id just *cough* "buy" a copy of that

---

### Post by Lunx on 2009-04-22
> **Sef said:**
> That is not true any more.  For one gigabyte ram, I would make a one gigabyte swap.


Thanks for the update, I wasn't aware of that. Why the change from past practice? Nearly everything I've read mentions the 1.5 to 2 times RAM thing, although lately I've noticed quite a few posts here and in other places which mention making it the same size as RAM.

---

