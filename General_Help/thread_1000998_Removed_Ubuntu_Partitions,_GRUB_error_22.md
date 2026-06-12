---
title: "Removed Ubuntu Partitions, GRUB error 22"
date: 2008-12-03
forum: General Help
---

### Post by mdszepher on 2008-12-03
Now that I have a portable version of Ubuntu, I decided to remove my copy of Ubuntu on my hard drive and join my new free space with the rest of the disk in a NTFS partition.  When I did this, I didn't realize that I'd be unable to reboot my machine, and now I receive a GRUB error 22.

I'm trying to edit GRUB, but I'm unable to find it.  I'm currently using a Live CD, and both the file system and the boot folder on one of my hard drives does not have a grub folder.

The computer now only has one OS, and it's Windows Vista.  Is there a way to find where GRUB is so I can edit it, or is there something I can do with my Vista CDs?

---

### Post by ajgreeny on 2008-12-03
First thing to do is restore the windows MBR.  I can tell you how to do that in XP, but I don't know about vista.  Google for the answer to that and I'm sure you'll find it.

The nest thing to do is search for your ubuntu install, so connect the external disk (I assume you mean you have an external disk with ubuntu installed) and then run the ubuntu liveCD.  Using that you can install grub to the external disk, leaving the vista MBR alone, so that if you boot the machine with the ubuntu disk not connected, windows will start automatically but if the external drive is connected grub will appear and you can choose windows or ubuntu.  You will need to set the boot order in your bios to the external drive first and internal drive second.

To install grub follow this:-
Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
   ```
 find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
   ```
 root (hd?,?)
```
[like : root (hdo,1) ,probably]
then:
   ```
 setup (hd0)
```
This is where your windows partition and MBR normally is, but you want grub on your external disk, so use hd1, etc as appropriate, which you can find in live CD by using **sudo fdisk -l** in the terminal and using the output for whichever is your external disk.  Remember that fdisk uses /dev/hdx# for partitions so you will need to translate that to grub speak, where sda will be hd0, sdb will be sd1 etc etc.
Then:
   ```
 quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

Good luck, I hope it all works out for you.

---

### Post by caljohnsmith on 2008-12-03
If your HDD only has Vista on it now, you can reinstall a Windows MBR (Master Boot Record) so that you should be able to boot directly into Vista again. You can do that from the Ubuntu Live CD by opening a terminal (Applications > Accessories > Terminal) and doing:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/[COLOR="Blue"]sda[/COLOR]
```
That assumes the Vista drive is sda, so change that if necessary. How about giving that a shot and let me know how it goes. :)

---

