---
title: "Install Lubuntu on separate disk next to WindowsXP on Dell 8200"
date: 2013-11-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gcravelli on 2013-11-07
I am a Linux beginner. I want to install Lubuntu on my Dell Dimension8200, with 2 diskdrives (a-disk 80GB and b-disk 40GB, memory 768MB). 
First I tried Ubuntu, but my PC lacks power. 
WindowsXP is on the a-disk.
The BIOS does not allow to boot from the b-disk.

I have installed Lubuntu and when I restart the PC I get an error:
Error: no such device : EE...........
entering Rescue Mode
Grub Rescue.

I don´t no what to do with Grub Rescue, so I have created a Boot Repair CD. With that CD I repaired WindowsXP MBR. Now I can restart WindowsXP.
But I cannot find Lubuntu on the b-disk.
More details of my configuration are available in the attachment and in [http://paste.ubuntu.com/6378016](http://paste.ubuntu.com/6378016).
Pleas tell me how to resolve this problem.

Attachment: extraxt of  [http://paste.ubuntu.com/6378016](http://paste.ubuntu.com/6378016)

---

### Post by Dennis N on 2013-11-07
Since you said you can only boot off the first drive (sda), grub bootloader has to be installed to MBR of **sda**. Your Boot info script shows grub bootloader is installed to MBR of **sdb**. 

Do the install again. Everything else about your install would be the same as the first try such as choosing the partitions on sdb for root and home after selecting "something else" for method of installation - except at the bottom of that same screen, you must choose in the little selector box where to put the bootloader - choose **sda** this time (with no number after it).

Then when you start up, you should see the grub menu allowing you to choose between Win XP and Lubuntu.

---

### Post by gcravelli on 2013-11-08
I did a new install off Lubuntu (lubuntu-13.10-alternate-i386, because my PC has a NVIDIA graphic card).
I skipped the network configuration, so there was no internet connection during install.
For disk partitioning i have choosen for guided, using the whole sdb disk. Automatically  two partitions were created (an ext4 and a swap partition).
The grub installation was in MBR of sda.

After install I restarted the system.. And again I got error messages:
Error: no such device : EE...........
entering Rescue Mode
Grub Rescue.

I restarted withe the boot repair disk (32 bits), and connected to the internet.
I did not perform any changes, but created the boot info [http://paste.ubuntu.com/6382717/](http://paste.ubuntu.com/6382717/)

The boot info shows:
============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .
 => No boot loader is installed in the MBR of /dev/sdb.
===================
And for sdb1:
sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img
========
Can anybody please tell me what is the problem is.

---

### Post by oldfred on 2013-11-08
I have seen several others with these old Dell that only boot from sda. Not sure what Dell did, but they just do not want to boot from sdb directly. I normally suggest installing the way you did with Windows on one drive and Ubuntu on the other.
If Dell will not let you boot from sdb, then the only choice is to install Ubuntu to sda. It may work with just a boot partition of 300MB on sda or a full / (root) partition. Then all you can do is use sdb for /home or shared NTFS data partition(s).

---

### Post by Dennis N on 2013-11-08
Could you boot Lubuntu with root and home both on sdb, if you specify a separate boot partition on sda and install the grub bootloader to mbr of sda? 

I'm guessing that the bootloader on the mbr on sda can only point to a partition on the drive it is installed on for the continuation of the boot to the appearance of the grub menu.

---

### Post by gcravelli on 2013-11-09
It works, with a boot partition on sda.

I executed the following steps:

[LIST=1]
[*]Execute boot repair to fix MBR on sda.
[*] Start WindowsXP and create a 1 GB partition on sda1.
[*] Followed the steps in article: [BootPartition]("https://help.ubuntu.com/community/BootPartition?action=fullsearch&value=linkto%3A%22BootPartition%22&context=180") (create a separate /boot partition at the start of the disk, and setup Ubuntu to use it)
[/LIST]

At the end of Boot-repair, there is a confusing message: *please do not forget to make your BIOS boot from sdb.* 
I installed everything to boot from sda. And  my Dell will not boot from sdb.
The boot information is in paste.unbutu.com/6387144.
When I start my PC it shows the GNU GRUB start menu (version 2.00 19Ubuntu2.1)
I can choose:

[LIST=1]
[*]UBUNTU
[*]Advanced functions for UBUNTU
[*]MS Windows XP Home Edition (on /dev/sda1)
[/LIST]

All 3 options can be started.

Dennis and Oldfred, thanks you for your help.
Now I can start to get to know the world of Linux Lubuntu.

---

### Post by Dennis N on 2013-11-09
> **gcravelli said:**
> It works, with a boot partition on sda.



Success! I was hoping that might work. Enjoy Linux.

---

