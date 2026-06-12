---
title: "Ubuntu doesn't recognize my HDD"
date: 2008-09-21
forum: Desktop Environments
---

### Post by Gamer6432 on 2008-09-21
My Windows died on me because of a chipset driver error. I burned Ubuntu on to a disc and am able to boot from it just fine. The problem is that it does not see my HDD, and thus I cannot back up any information.

I am using two Western Digital 250GB SATA hard drives in a RAID 0 configuration.

---

### Post by Pro-reason on 2008-09-22
Enter these commands in a terminal:

```

sudo fdisk -l
sudo blkid
cat /etc/fstab

```

---

### Post by Gamer6432 on 2008-09-22
It still won't show my HDD.

fdisk -l returns
```
Disk /dev/sda: 250.0 GB, 2550059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe2afe2a

   Device Boot     Start     End     Blocks     ID   System
/dev/sdal   *          1   60801   48838001      7   HPFS/NTFS

Disk /dev/sda: 250.0 GB, 2550059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1170168b

Disk /dev/sdb doesn't contain a valid partition table
```
sudo blkid returns
```
/dev/loop0: TYPE="squashfs"
```
cat /etc/fstab retunrs
```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
```

---

### Post by Pro-reason on 2008-09-22
> **Gamer6432 said:**
> It still won't show my HDD.
```

Disk /dev/sdb doesn't contain a valid partition table

```

I would suspect that this is the hard drive you are talking about.  It doesn't look good.

---

### Post by Gamer6432 on 2008-09-23
Technically, I"m talking about both of them. They're set up in a RAID 0 array, so the computer should see them as one drive. Currently it doesn't show anything.

Assuming the worst and there's no way to salvage data via ubuntu, would using an external enclosure work? There's very little I won't do to salvage the data these drives contain.

---

### Post by Pro-reason on 2008-09-23
I was about to say something positive, but then I looked [RAID 0]("http://en.wikipedia.org/wiki/RAID") up on Wikipedia, and read that &#8220;RAID 0 (striped disks) distributes data across several disks in a way which gives improved speed and full capacity, but all data on all disks will be lost if any one disk fails.&#8221;

You should, if possible, make an image of the contents of the drives, so that you can work on that image without doing anything further to the drives.  This will require another, larger drive.  Then do [data-recovery techniques]("https://help.ubuntu.com/community/DataRecovery") on the image.

---

### Post by Gamer6432 on 2008-09-24
> **Pro-reason said:**
> 
You should, if possible, make an image of the contents of the drives, so that you can work on that image without doing anything further to the drives.

OK. Can you give me a link for instructions on that? (Still very new at this.)

---

### Post by Pro-reason on 2008-09-24
> **Gamer6432 said:**
> OK. Can you give me a link for instructions on that? (Still very new at this.)

Try this guide: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem).

---

### Post by AnRkey on 2008-09-25
What RAID are you using, your motherboard's raid perhaps?

---

### Post by WWSmith36 on 2008-09-25
I have yet to find anyone that knows how to get ubuntu to recognize hardware raid configured throught the motherboard.  All I hear about is software raid / fake raid.

There is only one way I know of recovering that data.  I use Ultimate Boot CD for Windows. The only problem is the you have to build the CD yourself with the i386 directory from your windows install disk. Sound like alot of work but its worth it.

---

### Post by Gamer6432 on 2008-09-25
> **AnRkey said:**
> What RAID are you using, your motherboard's raid perhaps?

Yes, I use the RAID configuration on my motherboard. Asus M2N SLI Deluxe.

---

### Post by AnRkey on 2008-09-26
> **Gamer6432 said:**
> Yes, I use the RAID configuration on my motherboard. Asus M2N SLI Deluxe.

OK this should be quite easy to get around then. All you need to do is make your own Bartpe disk from an winblows XP cd. Bartpe Builder is an app that allows you to build a cd image from your winblows XP install disk, integrate drivers and boot from it for repairs/maintenance to your system.

Your onboard RAID is not easy to get working on Linux if at all. So you make a BartPE disk, add your drivers, boot up from the disk and backup your data. Then you can remove both drives from your onboard raid and use Linux raid instead. Since the onboard RAID is not proper hardware RAID anyway the performance should be close if not the same.

Here is the BartPE builder site >> [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)
and here is a link for setting up Software RAID on Ubuntu during install >> [http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

Some more advanced RAID info >> [http://wiki.randompage.org/index.php/DistOS:Linux:RAID#Using_Software_RAID_in_Linux](http://wiki.randompage.org/index.php/DistOS:Linux:RAID#Using_Software_RAID_in_Linux) (A bit more tricky)

Lastly here is the Ubuntu wiki page for FakeRAID >> [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Good luck,

R

---

### Post by Gamer6432 on 2008-09-26
It still refuses to show my HDD.


What are the chances I could salvage at least most of the data using a file recovery program if I just reinstalled the OS?

---

### Post by AnRkey on 2008-10-01
> **WWSmith36 said:**
> I have yet to find anyone that knows how to get ubuntu to recognize hardware raid configured throught the motherboard.  All I hear about is software raid / fake raid.

There is only one way I know of recovering that data.  I use Ultimate Boot CD for Windows. The only problem is the you have to build the CD yourself with the i386 directory from your windows install disk. Sound like alot of work but its worth it.

Yeah the onboard RAID that I have seen are all fake RAID or software RAID that is proprietary(closed source)

R

---

