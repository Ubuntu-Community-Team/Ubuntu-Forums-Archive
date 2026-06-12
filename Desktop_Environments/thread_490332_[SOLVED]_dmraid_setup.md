---
title: "[SOLVED] dmraid setup"
date: 2007-07-02
forum: Desktop Environments
---

### Post by fjgaude on 2007-07-02
I have an ASUS, AMD X2 box. I would like to try dmraid and Ubuntu, no Windows. I have four drives, and the mother board BIOS has both NVidia and Silicon Imgaes fakeRAID.

I've read many of the HOW-TOs about dmraid but too complicated because of dual-boot, etc. What if I boot from a single drive with Ubuintu already installed, but then have a RAID0 set for data mounted to the file system?

Any advice on how to proceed?

Thanks!

frank

---

### Post by kuja on 2007-07-02
Honestly you're probably better off with software raid or spending the cash to get a real hardware raid card. If you're set on using dmraid check this howto: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I would personally follow it's older way of doing it, as it's 100% reliable, but if you can get the easier way to work then by all means do so.  It may look long/complicated/intimidating but it's really not. Everything you need is there, and a fair amount of it is copy+pastable.

---

### Post by fjgaude on 2007-07-02
Okay, and thanks!

I have read over the How-To you pointed to but thought it too complicated. It's likely not after I understand the principles behind it. I could then likely do what I wish with dmraid, using either nvraid or sil raid. It is true that I would still have either nv or sil still active when I boot into Linux?

What can I use for software raid under Ubuntu? I remember that Fedora let me make a raid set at install time, but can't recall if Ubuntu permits such.

frank

---

### Post by Crakie on 2007-07-02
You can the create the raid set with the alternate install CD (not sure if the LiveCD supports it). Worked just fine on my rig :) But if you already have a working installation and only want a data partition on raid0, you don't need any install cd. You can use the mdadm command to assemble an array.

It's as easy as:
a) create two partitions of preferably equal size (make sure the type is Linux Raid Autodetect)
b) use mdadm --create /dev/mdx --level=0 --raid-devices=2 /dev/yyy /dev/zzz to create the array (where x,y,z is something I cannot know)
c) mount /dev/mdx /mnt/xx

Next boot, you can use mdadm --assemble /dev/mdx /dev/xxx /dev/xxx to reassemble the array. Getting it to reassemble automatically at every boot is a bit more work and involves creating a new initrd image. Let me know if you need help with that.

EDIT: if you go for a complete reinstall, you can have the installer handle all the work. In addition, you could put / on raid0 as well (as converting an existing partition into root is not impossible, but tricky at the very least).

---

### Post by fjgaude on 2007-07-02
> **Crakie said:**
> You can the create the raid set with the alternate install CD (not sure if the LiveCD supports it). Worked just fine on my rig :) But if you already have a working installation and only want a data partition on raid0, you don't need any install cd. You can use the mdadm command to assemble an array.
[...]

Next boot, you can use mdadm --assemble /dev/mdx /dev/xxx /dev/xxx to reassemble the array. Getting it to reassemble automatically at every boot is a bit more work and involves creating a new initrd image. Let me know if you need help with that.

Okay, this is what I was hoping to get, to learn... I'll report back if I need help, and when I have successfully done it.

I've installed mdadm and am reading the man pages now... will take a day or two before I have the time to figure it all out and try to get two drives up stripped, then get back with you.

I keep adding to this first note: what is Linux Raid Autodetect partition? I can do ext3 and the like but don't know this one.

Thank you!

frank

---

### Post by Crakie on 2007-07-03
> **fjgaude said:**
> I keep adding to this first note: what is Linux Raid Autodetect partition? I can do ext3 and the like but don't know this one.

I don't know what program you use for creating partitions, but I recommend cfdisk. After creating one, you get to select the type. You will be presented with quite a few options, Linux Raid Autodetect is one of them. Note that this has nothing to do with the filesystem. Incidentally, I forgot to mention you have to apply a filesystem yourself after creating the raid array :-\" (for reiserfs, use mkreiserfs, use mkfs.ext3 etc.)

Good luck, I'll check in occasionally to see if you require any further assistance.

---

### Post by fjgaude on 2007-07-03
I normally have been using Gparted. I'll look at cfdisk. Lots for me to learn and i should be playing with all this stuff on a box that has nothing important on it. Right now I using my main machine with much valuable data... will setup another box with two drives and play with that as I learn the in and outs of RAID.

Thanks for your help... it's just a matter of time before I get all this down.

Happy 4th.

frank

---

### Post by fjgaude on 2007-07-03
frank@sunshine:~$ sudo mdadm --detail /dev/md64
/dev/md64:
        Version : 00.90.03
  Creation Time : Tue Jul  3 07:22:23 2007
     Raid Level : raid0
     Array Size : 72292224 (68.94 GiB 74.03 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 64
    Persistence : Superblock is persistent

    Update Time : Tue Jul  3 07:22:23 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : f61d35c6:f7ebc706:a0f8169b:995327f7
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       49        1      active sync   /dev/sdd1

Now when I try to mount /dev/md64 I get this:

frank@sunshine:~$ sudo mount /dev/md64 /media/RAID
Password:
mount: wrong fs type, bad option, bad superblock on /dev/md64,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

frank@sunshine:~$ dmesg | tail
[   35.880000] Bluetooth: RFCOMM TTY layer initialized
[   35.880000] Bluetooth: RFCOMM ver 1.8
[   44.164000] eth1: no IPv6 routers present
[  330.000000] md: md_d1 stopped.
[  997.048000] cramfs: wrong magic
[  997.048000] EXT3-fs: unable to read superblock
[ 1066.848000] md: md_d1 stopped.
[ 1085.492000] md: md_d1 stopped.
[ 2578.188000] EXT3-fs: journal inode is deleted.
[ 2985.484000] EXT3-fs: journal inode is deleted.

I'm getting there... I think my problem is, first, I used these two drives in nVidia raid and, second, then I formatted them in Gparted to primary ext3. I believe the headers likely have something that mdadm doesn't like. Can't say for sure. Why can't I mount the array?

BTW, cfdisk shows the disks to be good: ext3, one primary partition, bootable if I selected such.

frank

---

### Post by fjgaude on 2007-07-03
Here's what dmraid shows:

frank@sunshine:~$ sudo dmraid -tay
/dev/sdc: "pdc" and "nvidia" formats discovered (using nvidia)!
/dev/sdc: "sil" and "nvidia" formats discovered (using nvidia)!
/dev/sdd: "sil" and "nvidia" formats discovered (using nvidia)!
nvidia_ffdafgab: 0 144607488 striped 2 128 /dev/sdc 0 /dev/sdd 0
ERROR: opening "/dev/.static/dev/mapper/nvidia_ffdafgab"

Interesting, eh?

frank

---

### Post by fjgaude on 2007-07-03
Okay, going back to an earlier post, "make the file system after building the raid set". Not sure from your post how to do that. Please help, I'm so close! <smile>

What a ride...

frank

---

### Post by fjgaude on 2007-07-03
I did it with this command:

frank@sunshine:~$ mkfs -t ext3 /dev/md64

Thanks man for getting me going and learning what I didn't as yet know.

Have a wonderful 4th in 'Nam.

frank

---

### Post by fjgaude on 2007-07-03
More good news. It seems that with Ubuntu 2.6.20-15 kernel I don't have to assemble the raid set after rebooting. I see in the init.d folder two sh files for mdadm, so... a line was already in mtab after I first assembled it. I added a line to fstab and all is automatic now.

Thanks again for getting me going.

frank

---

### Post by Crakie on 2007-07-03
> **fjgaude said:**
> Thanks again for getting me going.

frank

You are welcome :) Glad to be able to give that little nudge one occasionally requires - as you pointed out yourself.

---

### Post by fjgaude on 2007-07-03
Going further, could you recommend a disk speed, thru-put test? These two drives in raid0 with Silicon Image controller (fakeraid) used here tested sequential read at 109 MB/sec using the Windows Sandra program. Three of them went to 120 MB/sec. Now this is fast.

Curious to know what they are doing under Linux.

frank

---

### Post by fjgaude on 2007-07-04
Okay, using hdparm -tT I get 44MB/sec for one drive and 80MB/sec for two in RAID0 using mdadm... very good. The two drives I am using are old generation ones, compared to new Seagates.

frank

---

