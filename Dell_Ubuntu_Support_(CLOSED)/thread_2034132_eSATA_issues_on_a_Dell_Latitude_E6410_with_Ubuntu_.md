---
title: "eSATA issues on a Dell Latitude E6410 with Ubuntu 12.04"
date: 2012-07-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Clarenceadams on 2012-07-27
This is my first post on the Ubuntu forums, I'm not sure if this belongs in the Dell forum or the Hardware/Notebook forum :S

Here is my problem: I have a ThermalTake Blac X Duet hard drive dock and none of the drives are showing up at all when connected to either my laptop or the docking station for my laptop through an eSATA connection. It's not that they are not mounted, but that they are not being picked up by the OS at all. Here is the output of sudo fdisk -l:
```
clarence@clarence-Latitude-E6410:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0004cd21

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1457043455   728520704   83  Linux
/dev/sda2      1457045502  1465147391     4050945    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1457045504  1465147391     4050944   82  Linux swap / Solaris
```As you can see only my primary hard drive is detected and I have a working 80GB HDD connected to my laptop through an eSATA connection. I have the SATA operation setting in my BIOS set to AHCI so that eSATA will work.

I have also tried many solutions that I have found through google. One of them included installing the "scsitools" package and running```
/sbin/rescan-scsi-bus.sh
``` to rescan/refresh the scsi bus but all I get is```
bash: /sbin/rescan-scsi-bus.sh: No such file or directory
```I have also tried using another script I found to rescan/refresh the scsi bus which was ```
echo "- - -" > /sys/class/scsi_host/host0/scan
``` but all I get is ```
bash: /sys/class/scsi_host/host0/scan: Permission denied
``` even if I run it as a super user and if I run it when logged in as root it runs successfully but nothing changes, the drive still isn't detected.

Here is more information that may help you help me:

I know for sure that the eSATA port is functional on my laptop because I used it successfully many times while using Fedora 16.

I know the HDD is good because it was detected successfully on a Windows installation, and I know the eSATA cable is functional because it's the same one I used on the Windows installation.

The SATA host adapter is an Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)

When I was using Fedora 16, I updated to a 3.0 kernel and eSATA stopped functioning unless the HDD was already connected before the computer booted, so I just kept booting from a 2.0 kernel and it worked normally, so maybe it's because I'm using the 3.2.0-27-generic kernel.

Any help would be appreciated. If you have any other questions that will help you help me, ask away! Thanks in advance for any advice/help.

---

### Post by gerrman97 on 2012-10-22
is the hard drives laptop or desktop. if laptop i can help. if not, well ur best bet is talk to customer support. post a pic of computer and hard drive dock. 
have fun,
              Gerrman97

---

