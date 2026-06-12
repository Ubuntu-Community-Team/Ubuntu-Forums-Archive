---
title: "GRUB install failure RAID"
date: 2010-08-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rayray519 on 2010-08-24
I am installing 10.04 on a Dell XPS Gen 4 system, with on-board Intel RAID0 between 2 identical drives (148.76GB) with a 128k stripe size.  When the install gets to about 94% then I get an error:

Unable to install Grub in /dev/sda.
Executing 'grub-install /dev/sda' failed.

This is a fatal error.

Not sure how to solve this problem - any help would be appreciated.
Thanks,

Ray

---

### Post by rayray519 on 2010-08-24
I should mention the drives are 74GB WD Raptor drives.  The RAID chip is onboard with the Dell XPS Gen 4 systems.

---

### Post by latex001 on 2010-10-01
I am having the same issue on my end with 160gb raptors using intel matrix storage manager

---

### Post by ronparent on 2010-10-01
The error is not fatal unless you don't know how to reinstall grub. See: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

The grub install failed probably because the install program tried to install it to /dev/sda (this is the default). So, to avoid repeating the error, remember that grub has to be installed to the raid partition your system is installed to, and the boot loader has to be installed to the MBR of the overall raid array. You can 'ls /dev/mapper' from the root of your install to display the name of the array followed by the name(s) of the partition. Post if you need more help.

---

### Post by joeheim on 2010-10-03
Hi,

I' ve got pretty much the same problem. Every time I try to install ubuntu I receive this error message:

Unable to install Grub in /dev/sda.
Executing 'grub-install /dev/sda' failed.

This is a fatal error.

No chance to install it on another drive, even by following this instructions how to reinstall the grub.

My System is a 

Sony Vaio VPCZ128GGXQIntel® Core™ i7-620M processor 2.66 GHz with Turbo Boost up to 3.33 GHz Intel® HM57 Express Chipset
Quad SSD in RAID 0: 256 GB*3 (64 GB x 4, Serial ATA, RAID 0 support*4)
Mobile 82801 SATA Raid controller
4 ATA Samsung 64 Gb Solid-State Disks

Automatically controls Gfx mode: Dynamic Hybrid Gfx system


Might be a problem with the Quad SSD? But that is completely out of my comfort zone.


By the way, Windows 7 is pre installed on the system.


Thanks for your help.

---

### Post by ronparent on 2010-10-04
I'll repeat. Don't install a raid boot loader to a non-raid location (ie sda,sdb, etc). The symbolic links for the raid drive and partition for your system can be listed in /dev/mapper. The first item in the list (after control) is the raid drive. Items following are the partitions. Following the instructions for reinstalling grub 2 I listed in my previous post, you reinstall grub for a raid as follows:

Mount the raid partition your new Ubuntu is installed to -
> sudo mount /dev/mapper/<TargetRaidPartition> /mnt

Install and configure grub to boot on the raid -
> sudo grub-install --root-directory=/mnt/ /dev/mapper/<YourRaidDrive>
Above - make sure that is /mnt/

Unless your system is an exception and the above doesn't work a reboot of your system should place you in the grub menu. Good luck.

---

### Post by psusi on 2010-10-04
The installer has a drop down list of destinations to install grub to.  You need to change it from the default /dev/sda to your raid array, which will be /dev/mapper/blah_xxxx.

Also if you are not dual booting with windows, you are better off not using the fake raid, but rather conventional Linux software raid.  To do this, delete any arrays you have defined in your bios, and use the alternate installer to configure software raid arrays and install.

---

### Post by joeheim on 2010-10-04
Hi,

>  The installer has a drop down list of destinations to install grub to.    You need to change it from the default /dev/sda to your raid array,   which will be /dev/mapper/blah_xxxx . 
Gave it a try with no success

This is what i get from the drop down list:

/dev/mapper/isw_cgefbfjgfc_Ubuntu    Linux device-mapper (striped) (256.1 GB)
/dev/mapper/isw_cgefbfjgfc_Ubuntu1  Windows Vista (Loader)
/dev/mapper/isw_cgefbfjgfc_Ubuntu2  Windows 7 (Loader)
/dev/mapper/isw_cgefbfjgfc_Ubuntu3
/dev/mapper/isw_cgefbfjgfc_Ubuntu-1


Ubuntu1 is my Windows 7 Recovery partition (ntfs)
Ubuntu2 is my Windows 7 System reserved partition (ntfs)
Ubuntu3 is my ntfs Windows 7 

Not appearing:
Ubuntu4 the locigal partition with Ubuntu5 (ext4) and unbuntu6 (swap) which do not appear in the drop down menu

---

### Post by joeheim on 2010-10-04
Hi ,

further more

I tried

>  
ubuntu@ubuntu:~$ sudo fdisk -l

Unable to seek on /dev/sda
ubuntu@ubuntu:~$followed by
> 
ubuntu@ubuntu:~$ sudo blkid
/dev/mapper/isw_cgefbfjgfc_Ubuntu1: LABEL="Recovery" UUID="92A41A9DA41A83BF" TYPE="ntfs" 
/dev/mapper/isw_cgefbfjgfc_Ubuntu2: LABEL="System Reserved" UUID="765A1AE35A1AA043" TYPE="ntfs" 
/dev/mapper/isw_cgefbfjgfc_Ubuntu3: UUID="6CA61B95A61B5EC0" TYPE="ntfs" 
/dev/mapper/isw_cgefbfjgfc_Ubuntu6: UUID="2d8ffb47-df0d-431b-853b-89c744a9b93e" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="4ae64268-a2ae-455c-b782-95194f0e2fb3" TYPE="ext3" 
/dev/sda: TYPE="isw_raid_member" 
/dev/sdb: TYPE="isw_raid_member" 
/dev/sdc: TYPE="isw_raid_member" 
/dev/sdd: TYPE="isw_raid_member" 
/dev/sde1: UUID="C1ED-12A6" TYPE="vfat" 
/dev/mapper/isw_cgefbfjgfc_Ubuntu5: UUID="a6d07db0-18eb-42a2-bb12-e729d8cf7fa4" TYPE="ext4" 
so after

> 
ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_cgefbfjgfc_Ubuntu5 /mnt
and 

> 
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/mapper/isw_cgefbfjgfc_Ubuntu5
You have a memory leak (not released memory pool):
 [0x16bd1e0]
You have a memory leak (not released memory pool):
 [0x14991e0]
You have a memory leak (not released memory pool):
 [0x1ed9790]
You have a memory leak (not released memory pool):
 [0x22d3790]
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
You have a memory leak (not released memory pool):
 [0x1d9e7b0]
I've got this result, which actually leaves me very confused!

Any suggestions?

---

### Post by psusi on 2010-10-04
You want this one:


/dev/mapper/isw_cgefbfjgfc_Ubuntu Linux device-mapper (striped) (256.1 GB)

---

### Post by ronparent on 2010-10-04
psusi is absolutely correct. The command to install would be:
> sudo grub-install --root-directory=/mnt/ /dev/mapper/isw_cgefbfjgfc_Ubuntu
That should get you booting. The location you used was the partition you install the system to. That would apply only for special cases and would not be applicable for your situation

---

### Post by joeheim on 2010-10-07
Thanks for your help, I really appreciate it,

but it is getting weird now.

I did a fresh clean install, same problems during installation, so I went for install without grub to install it later.

>  ubuntu@ubuntu:~$ sudo blkid
/dev/mapper/isw_cgefbfjgfc_Ubuntu1: LABEL="Recovery" UUID="92A41A9DA41A83BF" TYPE="ntfs" 
/dev/mapper/isw_cgefbfjgfc_Ubuntu2: LABEL="System Reserved" UUID="765A1AE35A1AA043" TYPE="ntfs" 
/dev/mapper/isw_cgefbfjgfc_Ubuntu3: UUID="6CA61B95A61B5EC0" TYPE="ntfs" 
/dev/mapper/isw_cgefbfjgfc_Ubuntu6: UUID="96847f90-e869-452d-af2a-38c1a4337f16" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="76a7e4b7-80c8-4ead-ad1e-77b0d5f22425" TYPE="ext3" 
/dev/sda: TYPE="isw_raid_member" 
/dev/sdb: TYPE="isw_raid_member" 
/dev/sdc: TYPE="isw_raid_member" 
/dev/sdd: TYPE="isw_raid_member" 
/dev/sde1: UUID="AEAD-A8C8" TYPE="vfat" 
/dev/mapper/isw_cgefbfjgfc_Ubuntu5: UUID="7500df9b-5c36-4a96-8426-de46c02b813a" TYPE="ext4" 
 followed by

>  
ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_cgefbfjgfc_Ubuntu /mnt 
mount: /dev/mapper/isw_cgefbfjgfc_Ubuntu already mounted or /mnt busy
and

> 
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/mapper/isw_cgefbfjgfc_Ubuntu
/usr/sbin/grub-probe: error: cannot find a device for /mnt//boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
????

Never ever experienced any problems with my older notebooks and Ubuntu, but this new Sony Vaio Laptop drives me crazy.

---

### Post by psusi on 2010-10-07
Well if it says it's already mounted, then it seems it is already mounted... run mount by itself to see where.

---

### Post by psusi on 2010-10-07
Actually it looks like you tried to mount the entire disk.  You need a partition number on the end there.

---

### Post by joeheim on 2010-10-08
Hi,

I tried something completely different. 

Ubuntu 10.10 beta

Absolutely no problems during installation, grub install ok, dualboot with windows 7 working.

Of course a lot of other problems - black screen, touchpad etc.
I will looking into this matter later.

Really interesting is the fact, that a beta release of Ubuntu 10.10 is installing without any problem but Ubuntu 10.04.1 LTS (!!!!) not.

Strange world

Nevertheless, Thanks very much for your help, I m sure I will be back with other questions soon.

---

### Post by lindude on 2010-10-10
I tried 10.04 with the same sort of issues, (see attachment), but the help stuff is way out of my league. I also tried 10.10 which also failed grub wouldn't install.

Does anyone know of any simple howto's to follow to set up and partition my HDD in 2 partitions, one for OS and another for all my other stuff, in raid 0. 
I'm not interested in a Dual boot with Windows but would like to use Ubuntu 10.01 64bit.

I know very little about the in's and out's of how ubuntu works and can only really follow howto's


My system is a Dell M6500
Intel(R) Core(TM) i7-920 extreme
Genuine Windows(R) 7 ultimate 64bit 
16GB (4x4GB) 1333MHz DDR3 SDRAM
2.5 " 256GB FDE Solid State Drive 
2.5 " 256GB FDE Solid State Drive 
Blu-ray Disc Drive
NVIDIA QUADRO FX 3800M Video Card
Intel WiFi Link 5300 (802.11 a/g/n 3x3)

Thanks in advance.

---

