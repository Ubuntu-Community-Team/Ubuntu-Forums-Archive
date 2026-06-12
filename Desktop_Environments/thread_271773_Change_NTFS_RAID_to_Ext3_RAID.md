---
title: "Change NTFS RAID to Ext3 RAID"
date: 2006-10-05
forum: Desktop Environments
---

### Post by DOD1951 on 2006-10-05
I currently have raid 0 formatted as NTFS which contains all my music files.
I am running out of space where I have Dapper installed and now want to use NTFS RAID disks as Ext3 disk instead. I currently have the MP3 files on NTFS RAID and on my Dapper boot drive so want to have one copy, on Ext3 (Moving further away from Win XP everyday). Any ideas how to do it please? I have already backed up the MP3 files. The RAID set is currently "pdc-jjecchfi" is this likely to change after formatting?
Thanks in advance.

---

### Post by DOD1951 on 2006-10-11
I finally worked out how to do this and thought I'd share the experience.
I have an ASUS A7v333 motherboard with onboard Promise FastTrack133 Controller using the Promise chip PDC20276. I had a RAID0 setup as NTFS when using the array on Windows XP. After installing Ubuntu I found I was spending more time there to the point where I was hardly ever using Win XP so thought I'd use the RAID0 in Ubuntu. I downloaded the Gparted tool and setup the partition on the disks. I let Gparted guide me through that and ended up with one big partition over the 2 drives. I then used DMraid to build the RAID0 and ended up with a clean RAID0 ext3 partition. I have reloaded the 8000+ MP3 files onto this and so far everything works ok. The annoying thing is that RAID0 is not treated as a disk device in quite the same way as say /dev/hda1 or /dev/hdb1. It looks like this /dev/mapper/pdc_hefieaib1. I had to add the mount command into the /etc/fstab "/dev/mapper/pdc_hefieaib1 /mnt/raid ext3 defaults,errors=remount-ro 0 1" which must be wrong in someway as I get a warning of bad format on line 12 on boot up everytime but everything still works. As I'm quite new to all of this im not convinced i really have this setup correctly so I tried to use the Ubuntu alternate install CD and see if this would do a better job. A few interesting observations on trying this. I deleted the array at bootup of the PC, accepting that i would lose all data on the array. When I got to the setup RAID option on Ubuntu it said I didn't have any partition to build an array even though it showed me as having the disks in the partition manager. So i thought id lost all my data to achieve zero! Anyway I went back to what I had tried before and not only did I get the RAID0 working again, as above, but I also found that all the files were still there. So try as I might I didn't actually lose anything other than time. The other thing is that when you rebuild the array the pdc_name changes e.g the first time the name was pdc_jjecchfi the 2nd time it was pdc_hefieaib1. Think I still have a whole lot to learn!

---

### Post by Ai1dRo0kNotBot on 2008-02-09
Please excuse me for offtopic, but i've got Promise Fastrack-4060SX (the very same thing that ATA-133, but it has 4 ide channels, and it's raid-5 capable).
The question is: does your hardware work "out of the box", or there is some magic driver?

---

