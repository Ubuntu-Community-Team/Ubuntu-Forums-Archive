---
title: "Help.. my dell 1505 wont boot"
date: 2007-11-28
forum: Dell  Ubuntu Support
---

### Post by tochi on 2007-11-28
Hi guys,
   I am new to ubuntu. I recently installed ubuntu on my dell 1505. I got everything working except for my wireless. I was told i needed ndiswrapper to get it to work. I downloaded and was installing the application when my computer froze. I had to reboot manually but i am not sure if i hit the media direct button. Anyway, i go reboot and it gets stuck on the screen GRUB loading.. please wait. Error 16. I cant get past that screen. I tried reinstalling from the dvd but it just gives me so many errors and wont let me install it.

I tried using a windows cd to reformat the disk but here is the message i get.

IDE status : failed
Status Byte = 64
Control Code = 1
Msg = No additional sense info.
Error code: 10000-0141
Msg: No drive detected.

What do i do? How do i get my ubuntu back on? Its not a dual boot system just a single ubuntu installation. Thanks

---

### Post by Skuzniak on 2007-11-28
It sounds like you might have accidentally pushed the media direct button, it has been known to cause GRUB and hard disk errors. Did you choose to install to the largest free space in the Ubuntu installation, or did you choose Guided - Whole Disk?

If you can boot in to the Ubuntu live CD, run gparted and delete all the present partitions on your hard drive. Then, choose to install with Guided - Whole Disk. If you cannot boot into the live CD, try downloading something called the Ultimate Boot CD, and boot from that. There is a utility on there that will allow you to erase the hard drive partitions. Then pop in the Ubuntu CD and try installing again.

Edit: This may be of interest to you. If you want to permanately erase ALL data on your hard drive (including the Dell MediaDirect function), you can use this command from the live CD. If you do this, pushing the Media Direct button will not destroy your bootable partitions.

Very BIG WARNING, this will erase ALL DATA on your hard drive with no second chances!! Be sure you want to do it!

dd if=/dev/zero of=/dev/sda

The thread I took it from is here, if you want to find out more about MediaDirect.
[http://ubuntuforums.org/showthread.php?t=606345&page=2](http://ubuntuforums.org/showthread.php?t=606345&page=2)

---

### Post by tochi on 2007-11-28
I chose the guided whole disk installation. I cant boot into live cd, i downloaded the ultimate boot cd and booted from there but i dont know which utility i am supposed to use to erase the hard drive partitions.. There are over 20 utilites on there and i cant figure out which one to use.

I definitely want want to erase everything on the hard drive. thanks for the info.


> **Skuzniak said:**
> It sounds like you might have accidentally pushed the media direct button, it has been known to cause GRUB and hard disk errors. Did you choose to install to the largest free space in the Ubuntu installation, or did you choose Guided - Whole Disk?

If you can boot in to the Ubuntu live CD, run gparted and delete all the present partitions on your hard drive. Then, choose to install with Guided - Whole Disk. If you cannot boot into the live CD, try downloading something called the Ultimate Boot CD, and boot from that. There is a utility on there that will allow you to erase the hard drive partitions. Then pop in the Ubuntu CD and try installing again.

Edit: This may be of interest to you. If you want to permanately erase ALL data on your hard drive (including the Dell MediaDirect function), you can use this command from the live CD. If you do this, pushing the Media Direct button will not destroy your bootable partitions.

Very BIG WARNING, this will erase ALL DATA on your hard drive with no second chances!! Be sure you want to do it!

dd if=/dev/zero of=/dev/sda

The thread I took it from is here, if you want to find out more about MediaDirect.
[http://ubuntuforums.org/showthread.php?t=606345&page=2](http://ubuntuforums.org/showthread.php?t=606345&page=2)

---

### Post by Skuzniak on 2007-11-28
Ranish Partition Manager, Free FDISK and SPFDISK should all allow you to delete the partitions that were created by the Dell MediaDirect button. You can also use the utility Darik's Boot and Nuke or Active Killdisk to remove all data on the hard drive, then have Ubuntu set up the partitions after performing the erase all data command via terminal. Be sure to do the command I posted previously, otherwise any other accidental press of the media direct button will cause the same problem.

---

### Post by tochi on 2007-11-28
none of them works for me
:confused:

> **Skuzniak said:**
> Ranish Partition Manager, Free FDISK and SPFDISK should all allow you to delete the partitions that were created by the Dell MediaDirect button. You can also use the utility Darik's Boot and Nuke or Active Killdisk to remove all data on the hard drive, then have Ubuntu set up the partitions after performing the erase all data command via terminal. Be sure to do the command I posted previously, otherwise any other accidental press of the media direct button will cause the same problem.

---

### Post by Skuzniak on 2007-11-28
Are there any error messages when you try to run the utilities? Can you give us a better description than "none of them work"? It seems almost impossible to me that all of them fail to work, unless the Ultimate Boot CD cannot access the hard drive. Try changing the hard drive mode from AHCI to ATA (will require disabling flash cache module) in the BIOS, then check the utilities again. You can simply re-enable the flash cache and change the hard drive to AHCI again after wiping it. Windows XP can't see AHCI hard drives unless the proper driver is slipstreamed in, but Ubuntu has no problems with it.

---

### Post by tochi on 2007-11-28
all of them boot and then load..

it then gets to AUTOEXEC: copying A:\bin and A:\etc to Q:

A: is MEMDISK
UNPACK: Extracting "Q:\bin\UTILS.CAB"

this is where every single one of them gets stuck. All the utilities on the ultimate boot cd get stuck here.

I cant change anything in the bios, dell has it locked down.

DO you have aim or msn messenger?


> **Skuzniak said:**
> Are there any error messages when you try to run the utilities? Can you give us a better description than "none of them work"? It seems almost impossible to me that all of them fail to work, unless the Ultimate Boot CD cannot access the hard drive. Try changing the hard drive mode from AHCI to ATA (will require disabling flash cache module) in the BIOS, then check the utilities again. You can simply re-enable the flash cache and change the hard drive to AHCI again after wiping it. Windows XP can't see AHCI hard drives unless the proper driver is slipstreamed in, but Ubuntu has no problems with it.

---

### Post by Skuzniak on 2007-11-28
I have never even heard of that error before, google doesn't seem to turn up anything either. I know Dell locks down most of the fun features (like overclocking) in their BIOSes, but I've never heard of them locking it down so that you can't even change boot parameters. 

You can contact me on MSN, the username is in my profile.

---

### Post by b4d on 2007-11-29
Okay, first of all before you format, try booting the machine again with media direct button.

I tried that and it worked normally afterwards...

---

### Post by tochi on 2007-11-29
i tried that and it showed grub loading stage 1.5

grub loading.... please wait...
Error 16


> **b4d said:**
> Okay, first of all before you format, try booting the machine again with media direct button.

I tried that and it worked normally afterwards...

---

### Post by ntom-taylor on 2007-11-29
Try turning off the 'wireless' on the laptop if there is a button for it. I say this because i get the same error with my HP dv8000.

hope it helps.
Tom

---

### Post by tochi on 2007-11-29
did that.. no luck.. same thing


> **ntom-taylor said:**
> Try turning off the 'wireless' on the laptop if there is a button for it. I say this because i get the same error with my HP dv8000.

hope it helps.
Tom

---

### Post by tochi on 2007-12-03
anymore ideas?:mad:

---

### Post by nealron on 2007-12-28
**[SIZE="3"]I found a fix for the Dell Self-destruct-direct (MediaDirect) button problem.[/SIZE]** 

A little background info might be in order though. What the Dell MediaDirect button (next to the power button and has a house icon on it similar to an internet browsers "Home" button) does when the hard drive is partitioned in a way that it does not expect (aka, linux installed) it rewrites the partition table that it thinks it should have. Your partition table is essentially like the table of contents pages in a book with 100 billion pages, without it your screwed. 

What we're going to do here is offer a way to disable the button if you don't care about the data on the drive (like right after a fresh install) OR a way to recover your partition table with a nifty program called [testdisk]("http://www.cgsecurity.org/wiki/TestDisk").

**[SIZE="3"]Plan A - Disable Destruct Button[/SIZE]**
You can low-level format your hard drive to permanently remove the danger the button poses to your future data, because you _will_ loose ALL data currently on your drive. Issue the following command from a live CD/DVD booted system.

[B][SIZE="2"]****WARNING USE ONLY FROM LIVE CD/DVD******
****WARNING WILL DESTORY ALL DATA ON DISK*******[/SIZE][/B]
```
sudo dd if=/dev/zero of=/dev/sda
```

The above command writes zeros in every sector of your hard drive, aka "Zeroing the drive". Zeroing the drive has been known to overwrite the HPA (Host Protected Area) of the hard drive where the MediaDirect partition is hidden on the drive. Afterwards, pressing the self-destruct button will harmlessly show the MediaDirect splash screen and then boot GRUB.

[_The above came from Skuzniak here_]("http://ubuntuforums.org/showpost.php?p=3870754&postcount=2")

**[SIZE="3"]Plan B - RECOVER YOUR DATA[/SIZE]**.
If you have pressed the dreaded MediaDirect button and now have a very expensive paper weight for a laptop, FEAR NOT! testdisk to the rescue!

1) Boot up your live CD/DVD (like the one you used to install from).

2) Copy the additional repositories to your /etc/apt/sources.list file on your live CD/DVD session. The live CD isn't mean to install packages/programs to since it is erased when your reboot, however, if needed you can install a small amount of extra data. Like repair utilities. You can find instructions on how to do this [HERE]("http://kubuntuguide.org/Gutsy#Add_Extra_Kubuntu_Repositories").

3) Issue the following command to update your repository list after you changed your sources.list file and also install the precious data recovery utility "testdisk", as well as run testdisk after it's installed creating a testdisk.log file of all it's actions in the directory you issue the following command from.
```
sudo apt-get update && sudo apt-get install testdisk && sudo testdisk /log
```

4) Use the arrow keys to select your laptop hard drive. If you are using the live CD/DVD you should see two hard drives. 

**/dev/hda** (the live CD virtual drive) and **/dev/sda** (your laptop hard drive)

To "Proceed", tap the "Enter/Return" key when you've selected the appropriate hard drive.

5) Tap the "Enter/Return" key again on the next screen to select "Intel/PC" partition type.

6) Tap the "Enter/Return" key again on the next screen to "Analyse" (spelled the way it is in the program) your hard disk and search for your lost partitions.

7) This screen shows the screwed up partition table.. just tap the "Enter/Return" key again to "Proceed"

8) If you're lucky you'll see two or three partitions (If you let Ubuntu install configure your disk for you). Something like what you see below:
```
* Linux 0 1 1 18752 254 63 301266882
L Linux Swap 18753 0 1 19456 254 63 11309760
```
Tap the "Enter/Return" key again to "Proceed"

9) Now tap the right arrow key twice and tap the "Enter/Return" key to write the recovered partition table. Confirm it by taping the "Y" key and then the "Enter/Return" key.

10) Reboot your computer and take the live CD/DVD out. :)

NOTE: I had to do this twice for it to work for some reason, but after that, my precious Kubuntu booted up normal just like it used to without one file missing!

THANK YOU [_NICOLAE_]("http://ubuntuforums.org/showpost.php?p=3878125&postcount=7") and [_PSEUDOMANCER_]("http://ubuntuforums.org/showpost.php?p=3885747&postcount=8")!

---

