---
title: "Ubuntu 12.04.1 LTS not Installed Properly on my Dell E6520"
date: 2012-09-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by adscnet on 2012-09-03
Dear All,
I'm wondering if anyone come across this problem..

I have downloaded Ubuntu 12.04.1LTS (64bit) iso format & created the liveCD, booted my laptop from the liveCD & installed Ubuntu on it.

At the end of the installation it says installation completed, CD ejected & system rebooted. OK..

Now I should he the Grub menu asking me which OS to select to boot from .. this is NOT happening at all .. even my system switch automatically to Win 7 .. Grub menu is not showing at all, like never have Ubuntu installed !!

_**My System Specs & Bios Config:**_
- [Specs]: Dell E6520, i7 C2D 2.4GHz, 8GB RAM, 750GB HDD
- [OS]: Win7 64/b installed 
- [Partitions]: 4 available partitions: as follow:
---- 1 small part. for OEM (HDD bios tools/diag.) Primary type
---- 2 small part. for Recovery (I thing created by Win7) Primary type
---- 3 C part. 150GB (by me this has Win7 OS) Primary type
---- 4 D part. 200GB (by me this for data partition) Logic type
---- 5 Remaining unallocated size is about 350GB I left this for Ubuntu installation to do what ever it likes to do with it :)
Note: Ubuntu created only 2 partitions during installation one with 320gb & other with 7gb .. I don't know why .. Usually it creates more than 2 partition including SWAP partition (but I think in my case SWAP not created since I have big memory 8GB)

- [BIOS] RAID is on on SATA
- virtualization is on

I have stopped the virtualization and the RAID change it to AHCI & removed the Data partition & tried re-installing Ubuntu many times but same problem.

NOTEs: 
1. I noticed an error msg comes quickly & disappear when I boot from the LiveCD it says "error: Prefix is not set" then it shows the normal livecd boot menu normally.

2. Ubuntu try works fine
3. I have Ubuntu installed on other laptops with Win7 & no problem at all.

I think the problem with Grub is not installed/configured  properly !!

Any suggestions how to fix this?
Thanks.

---

### Post by 2F4U on 2012-09-03
Where did you install Grub, the boot loader?

[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

---

### Post by oldfred on 2012-09-03
If 2F4U's suggestion on reinstalling grub does not work:

I do not understand why RAID would be on if you only have one drive? Or do you have a new Intel Smart Response with an small SSD? RAID leaves meta-data on a drive and gparted or the installer will not work with RAID drives.

 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

Only run this if sure you do not want or have RAID:
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

Post these:
sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print

---

### Post by adscnet on 2012-09-04
> **2F4U said:**
> Where did you install Grub, the boot loader?

[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

I didn't choose custom installation. I let the setup finish normally, I'm not sure where the setup kept it.!

---

### Post by oldfred on 2012-09-04
Normally grub2's boot loader is installed to the MBR of sda. But the desktop install/liveCD does not have RAID drivers, so if you have RAID it cannot install grub to the MBR of the RAID.

Post the link to BootInfo so we can see details.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by adscnet on 2012-09-04
> **oldfred said:**
> If 2F4U's suggestion on reinstalling grub does not work:

I do not understand why RAID would be on if you only have one drive? Or do you have a new Intel Smart Response with an small SSD? RAID leaves meta-data on a drive and gparted or the installer will not work with RAID drives.

 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

Only run this if sure you do not want or have RAID:
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

Post these:
sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print

Unfortunately I'm not able to run the installed Ubuntu since my notebook boots me directly to Win7 partition w/o giving me any choice as I said above. 
I'll try the commands on the liveCD I don't know if this will work or not.

Note: I'll try that when I reach home. Also I need to try what 2F4U suggested.

---

### Post by adscnet on 2012-09-04
> **oldfred said:**
> Normally grub2's boot loader is installed to the MBR of sda. But the desktop install/liveCD does not have RAID drivers, so if you have RAID it cannot install grub to the MBR of the RAID.

Post the link to BootInfo so we can see details.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

I tried the BootRepair before but couldn't finish coz it was asking me for the internet connection & I didn't have access to internet at that day :(

---

### Post by YannBuntu on 2012-09-04
You can create a Boot-Info even without internet: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
It will open the report in a text viewer, then just copy/paste the report here.

---

### Post by adscnet on 2012-09-04
Thanks YannBuntu for the info I was running BR from a CD!!

I apologize guys, I used SCO Unix & Xinex before 19 years ago then I moved to Windows that is why I feel my self now like a baby learning how to walk!!

**_My Update:_** 
I run some commands to fix the GRUB2 & got a msg that installation completed & no error found .. but still not getting the GRUB menu.

Anyhow here is my [boot info url]("http://paste.ubuntu.com/1186163/")

One more thing plz: 
I'm thinking to remove Win7 & install Ubuntu on the system utilizing the full HDD, then install Win7 virtually using VirtualBox .. BUT since I'm into enterprise business development using Asp.net & MS-SQL etc. the question is.. is VirtualBox stable and can handle these requirements?

---

### Post by oldfred on 2012-09-04
Boot-Repair is reporting several issues or potential issues. 

You seem to have gotten duplicate sources.

You will need to chroot into your system to uninstall & reinstall grub and update the sources list. Boot repair has some helper ways to chroot.

If you just want to use liveCD and do it manually:
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

We also have seen issues on certain hardware with either very large / (root) partitions or where grub & kernel are higher on the drive. It is like the old issue with BIOS that could not boot past the first 137GB, but is something new. It may be a BIOS setting or bug in grub. First do chroot and see is system works. If not then we have to reconfigure with a separate /boot.

---

### Post by adscnet on 2012-09-04
Another update on this:
I tried what 2F4U suggested .. still no effect.
Also I did reinstallation with after running these commands
- sudo os-prober
- sudo dmraid -rE
again same problem it boot directly & go Grub.

Now I'll try what oldfred suggested with boot-repair

---

### Post by YannBuntu on 2012-09-05
> **oldfred said:**
> You seem to have gotten duplicate sources.

The "duplicate repositories" warnings at the bottom of the report are not issues, just noise. I'll try to hide them.

> **oldfred said:**
> We also have seen issues on certain hardware with either very large / (root) partitions or where grub & kernel are higher on the drive. It is like the old issue with BIOS that could not boot past the first 137GB, but is something new. It may be a BIOS setting or bug in grub. First do chroot and see is system works. If not then we have to reconfigure with a separate /boot.

I would bet on this.
More info: [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

---

### Post by adscnet on 2012-09-05
Guys this making me crazy ... 
last night I went bed after 3am because of the Boot-Repair .. after I run it, it displays the usual msg "Scanning systems.." & that took about 2 hours working & it didn't finish !!!!

Then I assumed the boot repair is getting stuck coz of the many installations I did before .. so I decided to erase the all HDD (don't worry) I have image copy of the factory settings, so image restored & did the Win7 fresh installation then ubuntu fresh installation ... God same problem .. also the Boot-Repair is staying in loop.

This didn't happen when I generated the boot-info before !!
Any suggestions plz.

---

### Post by YannBuntu on 2012-09-05
Sorry this infinite loop happens randomly with some people, and I don't know why. With some people the problem disappears after waiting several hours. I suppose this is related to one of the system tools (parted, fdisk, os-prober..) used by B-R at startup.
Some people solve the problem by either rebooting the PC or closing all windows then restart Boot-Repair.

---

### Post by adscnet on 2012-09-05
This link from "oldfred" solved the issue.

drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Thanks guys for your help.

---

### Post by oldfred on 2012-09-05
Glad you got it working.

Boot Repair does have a chroot helper. You still have to do part but it makes it easier.

---

### Post by adscnet on 2012-09-06
Yes great finally its working after a week of struggling :)

The Auto installation did only 2 partitions one main & another for the swap, the main part. is about 500GB .. I really hate this. 

In Windows usually I keep the system files on one partition coz it crashed often & keep the data in separate partition so it's easy and worry-less to format Win partition & install everything again of get it from image. 

What is the scenario in Linux (Ubuntu)? does the system crashed where it requires to re-install everything & the worst part to format the partition? 

If so, any partitioning suggestions?

---

### Post by YannBuntu on 2012-09-06
Hello
With Ubuntu:
1) you can reinstall the system without loosing documents, even if they are not on a separate partition: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

2) however it is safer to put the documents on a separate partition. I usually recommend 20GB for the system partition (mount point = "/"), and:
     -- a separate data partition (mount point = "/media/thenameyouwant"). 
     -- or a separate /home partition (/home contains application settings and data you will put in the Images/Videos/Documents.. folders you can see in the file explorer), but this can't be shared with Windows, and you need to choose different usernames if you want to share it with another Linux.

---

### Post by oldfred on 2012-09-06
My suggestion is similar to Yann's.

I always install to 25GB / (root) partitions. For new users I suggest the separate /home as that is handled automatically during install. But if dual booting with Windows I also suggest a shared data partition formated NTFS and the smaller system partition for Windows also. Windows seems to not like too much writing from foreign systems and the Linux NTFS driver exposes all the hidden files & folders that can lead to accidents. With a shared data NTFS partition you then can set the Windows system partition as read only.

I still have my shared NTFS with my Firefox & Thunderbird profiles so I had same email & bookmarks in both XP & Ubuntu. But then started installing the next Ubuntu into another 25GB and then created another data partition in Linux format. 

I now have /home as part of my 25GB / partition, but aggressively move all data to my two data partitions so I use 7 to 9GB in my Ubuntu installs.
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by adscnet on 2012-09-07
Hi,
It seems /home partition carries out all personal data + app settings, so when backup is done for /home it also will carry out the app settings backup too.

In Ubuntu does backing up the app settings has any benefits or not? In Windows I don't see this much helpful!

---

### Post by YannBuntu on 2012-09-07
among the app settings there are your emails, contacts, bookmarks... so better backup them!
[https://help.ubuntu.com/community/HomeFolder](https://help.ubuntu.com/community/HomeFolder)

---

### Post by adscnet on 2012-09-07
Great .. so I'm ending up with this scenario:

/boot - 50GB
/swap - 8GB I think this will be ok since I have 8GB RAM as well
/home - 470GB

---

### Post by oldfred on 2012-09-07
No.

If you want a separte /boot it only need to be 200 to 500MB. But /  which is root should be 25GB or more if you like. When you have a separate /home with all you data you may only use 6 to 8GB in / , but it is good to only use 25% or so to avoid issues. 
If writing a DVD you may need an extra 4GB in tmp for instance. I have accidentally run a backup and forgot to mount my /backup to it wrote into /. That could cause a crash if not enough extra room.

---

### Post by adscnet on 2012-09-07
> **oldfred said:**
> No.

If you want a separte /boot it only need to be 200 to 500MB. But /  which is root should be 25GB or more if you like. When you have a separate /home with all you data you may only use 6 to 8GB in / , but it is good to only use 25% or so to avoid issues. 
If writing a DVD you may need an extra 4GB in tmp for instance. I have accidentally run a backup and forgot to mount my /backup to it wrote into /. That could cause a crash if not enough extra room.

6 to 8GB for data in my case is nothing, currently I have about 70GB mixed between my customer developed systems (source codes), documents, manuals, a lot of downloads, virtual files (disks) for VitrualBox etc. ... 

Ok I may adjust to:
/boot - 50GB
/         -  500mb or 1GB (root)
/swap - 8GB  (_should I go to double this size to handle the hibernation_ )
/home - 200GB = ext4
/data - 270GB this partition to keep in it the virtual test or real VM boxes

Q1. /data, what ext?? it should be? 
Q2. can call it something else like /vituralbox or so.

---

### Post by adscnet on 2012-09-07
I found this 
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by oldfred on 2012-09-07
Do not confuse /boot with / (root) they are two different things. In a standard install /boot is just a folder inside / .

---

### Post by adscnet on 2012-09-07
> **adscnet said:**
> 6 to 8GB for data in my case is nothing, currently I have about 70GB mixed between my customer developed systems (source codes), documents, manuals, a lot of downloads, virtual files (disks) for VitrualBox etc. ... 

Ok I may adjust to:
/boot - 50GB
/         -  500mb or 1GB (root)
/swap - 8GB  (_should I go to double this size to handle the hibernation_ )
/home - 200GB = ext4
/data - 270GB this partition to keep in it the virtual test or real VM boxes

Q1. /data, what ext?? it should be? 
Q2. can call it something else like /vituralbox or so.

Any suggestion about the above?

---

### Post by oldfred on 2012-09-07
You have /boot and / reversed.

Otherwise fine. You will never use 8GB of swap. I find hibernation with Linux not worth much. It boots nearly as fast. If you have 8GB of RAM and want to hibernate it need to be 8GiB or somewhat more than 8GB, depending on who's calculating the numbers. Decimal vs. binary.

You can both label and mount other data partitions to just about any name you want. And label does not have to match mount point. Do not use spaces. I labeled a partition as 'Backup' and mounted it as 'backup' and forever had issues on which was which.

---

### Post by adscnet on 2012-09-07
Thank you so much oldfred and YannBuntu  for your help.

---

### Post by YannBuntu on 2012-09-09
> **oldfred said:**
> You have /boot and / reversed.

+1

For example, you can do:

/boot - 1GB
/ (root) - 50GB 
/swap - your RAM size
/home - 200GB = ext4
/data - 270GB this partition to keep in it the virtual test or real VM boxes

---

