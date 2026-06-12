---
title: "Mounting (at startup) a 2nd SATA Drive"
date: 2006-07-13
forum: Desktop Environments
---

### Post by LordofHaha on 2006-07-13
Running Ubuntu 6.06 - all updates installed. 

System Specs (Although this really shouldnt matter but just in case);
AMD Sempron Processor 2800+* (1.6GHz) 64bit ** Running Ubuntu 32bit **
GIGABYTE ATI Radeon X300SE 128MB
MSI Socket 754/ATI RS482/PCI-E/A&V&L Motherboard
HD 320G|WD 7K 8M SATA WD3200JDRTL R
HD 36.7G|WD 10K 8M SATA WD360GD %
MEM 512Mx2|D400 OCZ4001024V25DC-K R
-- Hard Drive Setup
hdd #1 aka /dev/sda: WD Raptor 37gb 
Partions: 
* sda1 - main partition with Ubuntu on it
* sda5 - swap partition 

hdd #2 aka /dev/sdb: WD regular old SATA 320gb
Partion
* sdb1 - main partition to be used for general storage (and eventually a House File Dump)

-- What I Did:
* Used a Knoppix CD (Version 4.something) and QTParted to create the partition table, the 1st partition and set it to active.
* Restarted and booted into Ubuntu to try and mount the drive via: System -> Administration -> Disks Manager
* Formatted the partition (ext3) with Disk Manager and had it mount to /mnt
* Clicked enabled, then try to browse - unable to write to so decided to open the terminal and force a CHMOD of 777 with the command:
```
sudo chmod 777 /mnt
```
* Was able to write a text file, open it, then delete it.
*** At this point in Time Ubuntu which had been updating itself in the background asked me to restart, so I did expecting to still find the drive at /mnt. To my surprise it wasn't there and I had to go through the whole setup again with Disk Manager, but this time I tried mounting to /home/zeus (a new folder in /home) as I thought there could have been a conflict using /mnt.
* Did a restart just to make sure the mount stuck but no luck on having sdb1 mount at startup.
* Next i tried explicitly using the command
```
sudo mount /dev/sdb1 /mnt/otherdrive
``` and got the error:
mount: mount point /mnt/otherdrive does not exist

-- What I want to do
* Have the 2nd drive mount at startup (no preference on location as worst case I can create a link to it) 
* This Drive should be accessible to all users on the PC (I am trying to initiate my siblings into Linux a little so being able to access any files on the drive be appreciated)
--

So any suggestions? on what to do to make sure this 2nd SATA drive mounts at startup (for all users)?

---

### Post by LordofHaha on 2006-07-13
Ok I think I solved my own problem... 

> **frodon said:**
> Nice, open your fstab file : ```
sudo gedit /etc/fstab
```Then add this line at the end of the file : ```
/dev/hdd1 /home/christopher/Desktop/2nd ext3 defaults 0 0
```And it should be ok, if you want to try if it works without rebooting use this command : ```
sudo mount -a
```This command run all the mount commands written in the fstab file.

-> I changed the /hdd1 to /sdb1 and the /home... to /media/OtherDrive
In order for me to get it into the /media folder, I did have to create the Directory first... which I think was my error when i had "mount point /mnt/otherdrive does not exist"

Anyhow consider this closed now I guess... :-#

---

### Post by ciscosurfer on 2006-07-13
You need to first create the directory that you want to mount sdb1:```
sudo mkdir /mnt/otherdrive
```There's no need to chmod the directory; it's "friendly" by default.
To allow the drive to mount at startup, add this line of code to your /etc/fstab```
/dev/sdb1 /mnt/otherdrive ext3 defaults,errors=remount-ro 0 1
```--mind the spaces in the above code...just copy and past it into your /etc/fstab file.  If you want it to mount immediately, issue:```
sudo mount -a
```and then check the /mnt/otherdrive directory to see your new files.  Otherwise, simply save your newly edited /etc/fstab file, close out, reboot.  You should be just fine when you start up again.  Cheers! :cool:

---

