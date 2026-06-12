---
title: "Help to use my other HD's"
date: 2009-02-10
forum: General Help
---

### Post by Imoen on 2009-02-10
I can't seem to access my other hard drives. I have an internal 200 gig SATA, an internal 160 gig slave and an external 400 gig. All are NTFS with files on them that I can not loose. When I attempt to mount any of them I get an message "unable to mount the volume, Operation not supported Mount is denied because NTFS is marked to be in use.

This is the information I get in terminal @ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c0e3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38537   309548421   83  Linux
/dev/sda2           38538       38913     3020220    5  Extended
/dev/sda5           38538       38913     3020188+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01f801f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x05c405c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       25841   195357928+   7  HPFS/NTFS

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd69c4e4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       48641   390708801    7  HPFS/NTFS


I also can not see these drives in Windows via VirtualBox. I am pretty new to using this OS, and don't want to have to go back to windows and buy vista. Could someone please help me resolve this?

---

### Post by oldos2er on 2009-02-10
"When I attempt to mount any of them I get an message "unable to mount the volume, Operation not supported Mount is denied because NTFS is marked to be in use."

 Usually you'll see this message when NTFS partitions have not been shut down properly. Ubuntu recognizes this, and attempts to preserve your data by refusing to mount them. Boot back into Windows, and do a clean shutdown.

---

### Post by Imoen on 2009-02-10
I can't boot back into windows. I had windows on my old HD and it died, so instead of buying a new drive and Windows Vista and upgrading half my computer I bought a new drive and installed Ubuntu on it.

Also on my external drive there is no shut down process, just pushing the power button is how it shuts down.

---

### Post by taurus on 2009-02-10
I guess you have to fix those ntfs partitions first before you can mount them unless you want to use the force option.

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
sudo ntfsfix /dev/sdc1
sudo ntfsfix /dev/sdd1
sudo mkdir /media/sdb1 /media/sdc1 /media/sdd1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
sudo mount -t ntfs-3g /dev/sdc1 /media/sdc1
sudo mount -t ntfs-3g /dev/sdd1 /media/sdd1
df -h
```

---

### Post by Imoen on 2009-02-10
kris@GrandPrix:~$ sudo apt-get update
[sudo] password for kris: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release [51.2kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages [296kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages [6843B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources [91.6kB]      
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources [2016B] 
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages [61.0kB] 
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources [15.5kB]  
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages [5200B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources [2366B]
Fetched 532kB in 9s (53.3kB/s)                                                 
Reading package lists... Done
kris@GrandPrix:~$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libntfs10
The following NEW packages will be installed:
  libntfs10 ntfsprogs
0 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
Need to get 391kB of archives.
After this operation, 950kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main libntfs10 2.0.0-1ubuntu2 [122kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main ntfsprogs 2.0.0-1ubuntu2 [269kB]
Fetched 391kB in 5s (72.1kB/s)    
Selecting previously deselected package libntfs10.
(Reading database ... 137647 files and directories currently installed.)
Unpacking libntfs10 (from .../libntfs10_2.0.0-1ubuntu2_i386.deb) ...
Selecting previously deselected package ntfsprogs.
Unpacking ntfsprogs (from .../ntfsprogs_2.0.0-1ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up libntfs10 (2.0.0-1ubuntu2) ...

Setting up ntfsprogs (2.0.0-1ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
kris@GrandPrix:~$ sudo ntfsfix /dev/sdb1
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... Failed to empty $FILE_LogFile/$DATA: Input/output error.
FAILED
Failed to reset $LogFile: Input/output error.
kris@GrandPrix:~$ sudo ntfsfix /dev/sdc1
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sdc1 was processed successfully.
kris@GrandPrix:~$ sudo ntfsfix /dev/sdd1
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sdd1 was processed successfully.
kris@GrandPrix:~$ sudo mkdir /media/sdb1 /media/sdc1 /media/sdd1
kris@GrandPrix:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb1 ntfs-3g force 0 0
kris@GrandPrix:~$ sudo mount -t ntfs-3g /dev/sdc1 /media/sdc1
kris@GrandPrix:~$ sudo mount -t ntfs-3g /dev/sdd1 /media/sdd1
kris@GrandPrix:~$ 

The SATA and my external worked on this. The drive that failed was the drive that had windows on it and died, causing me to switch to Ubuntu. I had hoped I might be able to access the drive as a slave just to save the data on it but I assume since it fails there's no hopes of that. 

Regardless, I thank you greatly for your help. These 2 drives that have worked is filled with the most important things (my children's photos and videos) so you have made me very happy.

---

### Post by taurus on 2009-02-10
```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
df -h
```

---

### Post by Imoen on 2009-02-10
OMG, that worked. Thank-you sooo very much. I don't think the drive is reliable for the future but at least I can save my important files.

---

