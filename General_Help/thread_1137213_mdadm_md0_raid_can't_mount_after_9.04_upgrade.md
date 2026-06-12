---
title: "mdadm md0 raid can't mount after 9.04 upgrade"
date: 2009-04-25
forum: General Help
---

### Post by jackthecruel on 2009-04-25
Hi guys,
I would really appreciate your input on a problem I'm having with my raid0 partition.
Everything was working fine before the upgrade, but now I'm getting:
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

when I try to mount.
So I tried to assemble md0 again, which gives the following:
sudo mdadm --assemble /dev/md0 /dev/sda3 /dev/sdb1
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has no superblock - assembly aborted
Checking mdstat I get:
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md_d0 : inactive sdb1[1](S)
      471539776 blocks

unused devices: <none>

Seems to me there's something wrong with sdb1 but examining it gives:
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 87a32e90:6e695d1b:fba291f5:9f1335ea (local to host Voldemort)
  Creation Time : Mon Dec  8 21:46:11 2008
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Mon Dec  8 21:46:11 2008
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : cc69b265 - correct
         Events : 1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        3        0      active sync   /dev/sda3
   1     1       8       17        1      active sync   /dev/sdb1

Also examining sda3 gives:
/dev/sda3:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 87a32e90:6e695d1b:fba291f5:9f1335ea (local to host Voldemort)
  Creation Time : Mon Dec  8 21:46:11 2008
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Mon Dec  8 21:46:11 2008
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : cc69b255 - correct
         Events : 1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        3        0      active sync   /dev/sda3

   0     0       8        3        0      active sync   /dev/sda3
   1     1       8       17        1      active sync   /dev/sdb1

I would guess both of those look fine. So I don't really know how to proceed. I've read that mdadm create is smart and will try to recreate existing raids, but that seems like a pretty risky move to me and I'd rather have your input before I do that.
Please don't assume I've checked/done something, this is my first time dealing with raid.
Any feedback is very much appreciated!
Thanks!

Emil

---

### Post by Einmaliger on 2009-04-25
Same problem here. Have a mdraid consisting of /dev/sd{b,c,d}1, and it worked perfectly until I updated to Ubuntu 9.04.

The funny thing is that it's not always /dev/sdb1 that mdadm claims to be busy - sometimes it's /dev/sdc1 or /dev/sdd1. But it's always exactly one of the three partitions.

With Google I found a workaround:

```
sudo losetup /dev/loop0 /dev/sdb1
sudo losetup /dev/loop1 /dev/sdc1
sudo losetup /dev/loop2 /dev/sdd1
sudo mdadm --assemble /dev/md0 /dev/loop{0,1,2}
```

After this, the RAID works again flawlessly. However, when repeating the sequence, mdadm inexplicably starts a rebuild, slowing down the system for several hours and probably aging the hard drives. I don't see why the rebuild is done - No drive is reported to be faulty; the reason that mdadm gives (in /var/log/syslog) is simply "raid array is not clean".

---

### Post by fastpakr on 2009-04-25
Having the same issue here after upgrade to 9.04 (64 bit).  Two disk raid 1 array, always get 'device or resource busy' then 'has no superblock' errors.  Not sure how to test the second poster's commands - not familiar with 'loset' command.

Edit - this worked for me:
mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf

Had to run it as root (not just prefix with su) to get it to work.  Raid array came up fine on reboot.

---

### Post by Einmaliger on 2009-04-25
You're right, there is no loset command. I meant losetup. Sorry, I typed that from memory.

I corrected that in my post.

---

### Post by jackthecruel on 2009-04-25
> **fastpakr said:**
> Having the same issue here after upgrade to 9.04 (64 bit).  Two disk raid 1 array, always get 'device or resource busy' then 'has no superblock' errors.  Not sure how to test the second poster's commands - not familiar with 'loset' command.

Edit - this worked for me:
mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf

Had to run it as root (not just prefix with su) to get it to work.  Raid array came up fine on reboot.

Worked for me too (also had to run as root). Thanks a lot!

---

### Post by shredswithpiks on 2009-04-25
This worked for me! It seems the upgrade wiped out the mdadm.conf file, so the raid stuff didn't get automagically sorted at boot time.

It was driving me nuts, though, because I was trying to import my 3-disk raid5 set and two of the disks worked just fine but one just wouldn't let itself get added back into my array.

Anyway, fixed the mdadm.conf file and rebooted and now everything is peachy... except that I got 2 of the disks to work and now the 3rd has to rebuild itself :(


Thank you so much, though!!!!

---

### Post by fjgaude on 2009-04-25
It seems that 9.04 gives an existing raid array a new UUID, one that is different from the one in the old mdadm.conf file.

I'll be doing testing tomorrow to make sure what is happening and will report back here.

---

### Post by shredswithpiks on 2009-04-25
ok... raid array totally didn't survive a reboot :(

re-assembled the array, had to add back that 3rd disk and it's rebuilding again. I'm gonna wait for it to rebuild, then recreate the mdadm.conf file just to make sure and see if it survives another reboot or not.

Of course, I'm gonna sleep while all this is going on so I'll post back tomorrow as well :/

---

### Post by Einmaliger on 2009-04-26
> **fastpakr said:**
> Edit - this worked for me:
mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf

Had to run it as root (not just prefix with su) to get it to work.  Raid array came up fine on reboot.
Confirmed. This fixed the problem for me. To be sure, I added another line to /etc/mdadm/mdadm.conf that described what disks belong to the array:
```
DEVICE /dev/sdb1 /dev/sdc1 /dev/sdd1
```

---

### Post by shredswithpiks on 2009-04-26
To clarify: should the DEVICE /dev/(partions...) line go before or after the ARRAY /dev/md0 (UUID stuff) line?

---

### Post by fjgaude on 2009-04-26
> **shredswithpiks said:**
> To clarify: should the DEVICE /dev/(partions...) line go before or after the ARRAY /dev/md0 (UUID stuff) line?

It's normal to have the DEVICE first, but I don't think it makes any difference. I always simply used what was auto created by **mdadm**.

---

### Post by fjgaude on 2009-04-26
Okay, I'm in Jaunty now... the only thing I did was remove mdadm and the mdadm.conf file, reboot. Re-install madadm and run this:

```
sudo mdadm --assemble --scan
```

My array was assembled and a new mdadm.conf file created. This is what I've been doing for years as upgrades come along and has always worked.

I'm sure this will work also:

```
mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

Now to get Firefox to play media. <smile>

---

### Post by decibyte on 2009-04-28
> **fastpakr said:**
> this worked for me:
mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf

Had to run it as root (not just prefix with su) to get it to work.  Raid array came up fine on reboot.

This also worked for me. Thank you very much. You just saved my day. Now I'm able to sleep tonight.

---

### Post by tomgibson on 2009-05-06
Thanks, this also fixed my problem on a fresh install of 9.04. I was tearing my hair out before recreating and rebuilding the array cause I thought it was to do with a mistake I had made in the configuration.

---

