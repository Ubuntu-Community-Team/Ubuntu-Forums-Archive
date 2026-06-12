---
title: "(Help) Install Ubuntu on Dell XPS 15 2012"
date: 2014-02-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Nam_Vu on 2014-02-16
I am a newbie and very excited with Ubuntu but I wonder how to install Ubuntu on my Dell XPS (installing on SSD cache) ? I decided to delete all Windows 8 and i will use ssd as System drive of Ubuntu, HDD will be the storage disk(music,video,v.v...). Does it need to disable something before installing ? I have not put LiveUSB to install cuz i am scared of losing my data and breaking the laptop => no device for working :(. Anyone help me ?

---

### Post by bc.haynes on 2014-02-17
You do need to be absolutely sure that you want to delete Windows before proceeding.

[[color=red]Linux is not Windows[/color]](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by oldfred on 2014-02-17
And we get many users who come back and say they have one application that only runs in Windows that they must have and want to dual boot. If you erase Windows you have to purchase a new copy. Best to dual boot.

But either dual boot or total install, you should make a full backup.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

      
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

   
 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

      
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

      
 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by Nam_Vu on 2014-02-18
> **oldfred said:**
> And we get many users who come back and say they have one application that only runs in Windows that they must have and want to dual boot. If you erase Windows you have to purchase a new copy. Best to dual boot.

But either dual boot or total install, you should make a full backup.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

      
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

   
 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

      
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

      
 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

> **bc.haynes said:**
> You do need to be absolutely sure that you want to delete Windows before proceeding.

[[COLOR=red]Linux is not Windows[/COLOR]]("http://linux.oneandoneis2.org/LNW.htm")

I will wipe out all Windows system, not Dual Boot. Can i install it on 32GB SSD disk (it is cache drive in Windows) ? And which steps i have to follow ? Tks.

---

### Post by oldfred on 2014-02-18
Are you planning on installing in UEFI mode or BIOS boot mode. 
Some with very new Dell's are having some graphic issues with Intel graphics. Is yours just Intel or dual video.

You will need to make sure you turn off Secure boot, fast boot and Intel SRT. Some are Windows settings and some are both UEFI & Windows.
You will need to remove the RAID meta-data from drives. Another user posted this:
       > Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

If you want UEFI, then you have to partition with gpt. Ubuntu will boot from gpt partitioned drives with UEFI or BIOS, but Windows only boots from gpt with UEFI.
If you want BIOS boot, you have to use MBR(msdos) partitioning. Both Ubuntu & Windows only boot in BIOS mode from MBR.
If UEFI you need an efi partition, if gpt with BIOS boot you need a bios_grub partition. I suggest both on both drives if using gpt. They are not large.

Usually the small SSD is mSATA. I do not know if that is really different from standard SSD or not.
I have both / (root) and include /home, but no data in my SSD. I have two / partitions of about 28GB on my 64GB one for current & one future. I use about 11GB of the 28GB and /home is 2GB but most of that is .wine for Picasa. And of the normally hidden folders that starts to have data gets moved to my data partition on my rotating drive.

Some suggest having swap, /home or other system partitions on hard drive. Newer SSDs should have similar lives to hard drives, so I just configure it like normal, but do add settings to reduce writes, use ext4 partitioning but turn journal off on SSD partition and set a cron job to run trim. You will need AHCI on in UEFI/BIOS.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

You have to decide which partitions you want on which drives. This is a standard suggestion. But I would use gpt and have efi partition and/or bios_grub on both drives at start of drive.
      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Nam_Vu on 2014-02-20
> **oldfred said:**
> Are you planning on installing in UEFI mode or BIOS boot mode. 
Some with very new Dell's are having some graphic issues with Intel graphics. Is yours just Intel or dual video.

You will need to make sure you turn off Secure boot, fast boot and Intel SRT. Some are Windows settings and some are both UEFI & Windows.
You will need to remove the RAID meta-data from drives. Another user posted this:
       

If you want UEFI, then you have to partition with gpt. Ubuntu will boot from gpt partitioned drives with UEFI or BIOS, but Windows only boots from gpt with UEFI.
If you want BIOS boot, you have to use MBR(msdos) partitioning. Both Ubuntu & Windows only boot in BIOS mode from MBR.
If UEFI you need an efi partition, if gpt with BIOS boot you need a bios_grub partition. I suggest both on both drives if using gpt. They are not large.

Usually the small SSD is mSATA. I do not know if that is really different from standard SSD or not.
I have both / (root) and include /home, but no data in my SSD. I have two / partitions of about 28GB on my 64GB one for current & one future. I use about 11GB of the 28GB and /home is 2GB but most of that is .wine for Picasa. And of the normally hidden folders that starts to have data gets moved to my data partition on my rotating drive.

Some suggest having swap, /home or other system partitions on hard drive. Newer SSDs should have similar lives to hard drives, so I just configure it like normal, but do add settings to reduce writes, use ext4 partitioning but turn journal off on SSD partition and set a cron job to run trim. You will need AHCI on in UEFI/BIOS.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

You have to decide which partitions you want on which drives. This is a standard suggestion. But I would use gpt and have efi partition and/or bios_grub on both drives at start of drive.
      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

I will delete all Windows and only use Ubuntu on my laptop, it is Dell XPS 2012 L521X, with dual graphics and UEFI support(my mSATA is 32GB which is cache drive). Thought, i will install it on mSata to reach the super speed. But i wonder if it can be installed on mSSD or not :(, I'm very busy so i afraid of losing time when installing fail :(.

---

### Post by oldfred on 2014-02-21
Installing an operating system is not just like installing a application. And new UEFI systems have been made more complicated, so you must review process. You may need to change some settings in UEFI/BIOS, install some drivers or make special settings.

If a new Linux user, it is much better to dual boot.

Another with suggestions on Video.
 Dell 15Z video settings with 13.10 gnome
[http://ubuntuforums.org/showthread.php?t=2194162](http://ubuntuforums.org/showthread.php?t=2194162)

---

