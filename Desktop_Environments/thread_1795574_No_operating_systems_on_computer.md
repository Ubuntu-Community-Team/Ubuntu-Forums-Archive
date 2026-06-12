---
title: "No operating systems on computer"
date: 2011-07-02
forum: Desktop Environments
---

### Post by ben44b on 2011-07-02
I "experimented" with UNetBootInstall on a USB key and messed up my GRUB2 settings pretty good. Now I can't find a grub.cfg file.

I've gotten a couple of error messages about not having an OS installed on the computer. 

I have Natty Narwhal installed as well as Windows 7 with Wubi.

Any help is much appreciated.

Thanx

---

### Post by mikewhatever on 2011-07-03
What were you trying to boot when you got that error?
Since Ubuntu is installed with Wubi, all its files are in a virtual file system (including grub.cfg), so it's not that easy to get to them.

---

### Post by Rubi1200 on 2011-07-03
Hi ben44b,
the best thing to do so we can see what is going on is the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by ben44b on 2011-07-03
Thanx for the help.

Here is the RESULTS.TXT:


```
       Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc 


```

---

### Post by Rubi1200 on 2011-07-03
If these results are correct, you have no operating system installed on the computer.

How did it get to this state? When you say, "experimented," what was supposed to be installed?

---

### Post by ben44b on 2011-07-03
I installed UNetBoot from the Software Centre. I thought I could load it onto a USB stick and try a different distro (Mandriva). 

I stopped when I realized that it wanted me to install it on the hard drive.

---

### Post by Sef on 2011-07-03
> I installed UNetBoot from the Software Centre. I thought I could load it onto a USB stick and try a different distro (Mandriva). 

I stopped when I realized that it wanted me to install it on the hard drive.

It seems that what was on your hard drive has been overwritten. To get it back, download [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk"). It can recover lost oses.

---

### Post by Rubi1200 on 2011-07-03
Here is a guide to using Testdisk:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Please read it carefully before starting!

---

### Post by ben44b on 2011-07-03
OK. Succeeded in getting back Windows 7 but not with the backup option. That was the big one. I'll just have to re-install Ubuntu, I guess.

Thanx for the help all.

---

### Post by jvgeli on 2011-07-08
LOL. it wiped everything. experimented is the right term.

---

### Post by ben44b on 2011-07-08
> **jvgeli said:**
> LOL. it wiped everything. experimented is the right term.

Yeah, that's why I used that word.

---

