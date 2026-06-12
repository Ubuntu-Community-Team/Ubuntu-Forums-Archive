---
title: "New Install with old RAID array"
date: 2009-01-19
forum: General Help
---

### Post by justtech on 2009-01-19
I have a RAID 1 array over two 500 gb hard drives.  I have been running Ubuntu for about 3 years now and unlike Windows, never had to format and reinstall... well, for some reason, I decided I wanted a clean install so I broke down and formated and reinstalled the latest version of Ubuntu this weekend.  When I got back up and running, I tried building my RAID array back up.  I can't figure it out and that is why I am here.  Now I am getting a error for a bad superblock and magic number.  Anyone know how to get this back up and running?  Hopefully with all of my old data on those drives?

---

### Post by justtech on 2009-01-19
K... still searching and trying to get this fixed.  Here is some more info just incase it helps someone solve the problem....

When I type in the terminal the following code:
```
sudo mount /dev/md0
```

I get the following error:
```
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

The when I type this in the terminal...:
```
sudo mdadm -D /dev/md0
```

I get this:
```
/dev/md0:
        Version : 00.90
  Creation Time : Sun Jan 18 21:57:13 2009
     Raid Level : raid1
     Array Size : 488386496 (465.76 GiB 500.11 GB)
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jan 18 23:30:43 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : fa79ab49:cfcee46d:8d101d1c:846599fc (local to host justtech-desktop)
         Events : 0.4

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       48        1      active sync   /dev/sdd

```

---

### Post by b0b138 on 2009-01-19
Not that my answer has anything to do with raid, but don't you need a mount point?  sudo mount /dev/md0 /mount/point

---

### Post by justtech on 2009-01-19
Sorry about that... same thing with the mount point.

---

### Post by fjgaude on 2009-01-19
If the drives were ever in a raid array they have to be removed by failing them, removing, unmounting the array, then stopping the array. And finally zeroing the superblocks. Then you can create a new array. Did you do these thing when you built the new array?

---

### Post by justtech on 2009-01-19
First of all, THANK YOU very much for the reply.  

To answer your question, no Sir, I have not failed them, removed them, etc.

In fact, the process that I had taken after the clean install was just following the same "How To Software RAID" that I did with my other install on a seperate HDD.  With this information on these RAID drives being so valuable to me, I chose to put a different Master HDD in and format and install on it and have my old one as a backup just incase something went wrong.  Problem is, when I put my old HDD back in, the RAID array still can't be mounted and I get all the same errors.

Can you point me in the right direction to the steps that you reccomend to recover this array?

---

### Post by fjgaude on 2009-01-20
Okay, from the looks of the --detail you have a good array. At least **mdadm** thinks so.

Try --force assembling the array and see what happens:

```
sudo mdadm --assemble -f --scan
```

If this doesn't do it, show us what the mdadm.conf file looks like.

---

### Post by justtech on 2009-01-20
Once again, thanks for the help.

I typed in:
```
sudo mdadm --assemble -f --scan /dev/md0 /dev/sdb /dev/sdd
```

And got this:
```

mdadm: /dev/md0 has been started with 2 drives.
mdadm: /dev/sdb not identified in config file.
mdadm: /dev/sdd not identified in config file.

```

Output for mdadm.conf file
```
sudo cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=fa79ab49:cfcee46d:8d101d1c:846599fc
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=11a07c71:c179a087:8d101d1c:846599fc

# This file was auto-generated on Mon, 19 Jan 2009 18:30:58 -0500
# by mkconf $Id$

```

And the output for fstab:
```
 cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1445b575-574d-4b43-a6c5-ba2935e0b247 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5d49ed04-3181-4b5d-b0c0-6955ad1aa7b7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/md0        /media/raid       ext3    defaults,relatime         1 2

```

---

### Post by fjgaude on 2009-01-21
Well, with two different UUIDs for the same array, yes, we have issues!

Take a look at this link and see if it might be useful:

[http://radu.rendec.ines.ro/howto/raid1.html](http://radu.rendec.ines.ro/howto/raid1.html)

Keep us informed as to how you are doing.

---

### Post by justtech on 2009-01-21
Sorry about this... you asked me to let you know how I was doing so here I am again.  I read through the page you sent the link too with no luck.  I continued my google search and have tried many many MANY things since.  I'm not exactly sure what all I have done tonight but the last forum that I ended up on from my Google searches, I ended up following what that guy had done and it seemed to fix his similar problem... This is what I have done  and where I stand as of tonight...

```
 sudo mdadm --create /dev/md0 -v -l 1 -n 2 /dev/sdb /dev/sdd
```

Which I then ended up with this..
```
 sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Wed Jan 21 20:13:31 2009
     Raid Level : raid1
     Array Size : 488386496 (465.76 GiB 500.11 GB)
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jan 21 21:47:33 2009
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 6169aaf2:8fe4bc21:8d101d1c:846599fc (local to host my-desktop)
         Events : 0.7

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       48        1      active sync   /dev/sdd
:~$ sudo mdadm --examine /dev/md0
mdadm: No md superblock detected on /dev/md0.

cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdd[1] sdb[0]
      488386496 blocks [2/2] [UU]
      
unused devices: <none>

sudo mdadm --stop /dev/md0
mdadm: stopped /dev/md0

:~$ sudo mdadm --assemble /dev/md0 /dev/sdb /dev/sdd
mdadm: /dev/md0 has been started with 2 drives.

dmesg | tail
[ 7696.470370] md: md0 stopped.
[ 7696.470608] md: unbind<sdd>
[ 7696.481042] md: export_rdev(sdd)
[ 7696.481051] md: unbind<sdb>
[ 7696.497041] md: export_rdev(sdb)
[ 7698.919652] md: md0 stopped.
[ 7699.303804] md: bind<sdd>
[ 7699.303949] md: bind<sdb>
[ 7699.560294] raid1: raid set md0 active with 2 out of 2 mirrors
[ 8028.542108] VFS: Can't find ext3 filesystem on dev md0.

```

Hopefully you can notice something or suggest something for me to try.  I'm getting really desperate.  Thanks for all your help.

---

### Post by fjgaude on 2009-01-22
Two things: you don't use --examine on an array but on a specific drive of an array. You didn't show that you put a filesystem on the array after you created it, did you?

From the --detail command the array is correct.

---

### Post by justtech on 2009-01-22
Put a  file system on the array as in format? I was really trying to bring back my
RAID array without losing my files. Any suggestions?  Have anything else I can try?

---

### Post by fjgaude on 2009-01-22
Okay, no you already have a filesystem installed, my mistake.

The only thing I can think of is one of your drives is bad, has gone bad. Just because the array looks good to **mdadm** and --detail doesn't mean that a drive isn't really, really bad.

But, try this: **umount** the array, **stop** it, and then run **fsck** on it from the bootup or from a liveCD:

```
fsck -t ext3 /dev/md0
```

When you used --create on the two drives that could have killed the data, but I've never done such before. You could be lucky. Of course that is why at first I thought you would need to add the filesystem.

Let us know how things go.

---

### Post by justtech on 2009-01-22
I just wanted to tell you thank you for all of your help over the past week.  Very appreciated.  Good news is I've recovered all of my files.  Bad news is, I was unable to build the RAID array back up just yet.  I have taken and added one of the two HDDs to the fstab file and then just mounted one of my drives in ext3 format.  Found all of my files which was a huge and I mean HUGE relief.  I'm currently backing them all up on other drives and then I will build the RAID array back up from scratch with formatting them and all and then putting all of my files back.  

So, once again, many MANY thanks to you for all of your time and help.

---

### Post by fjgaude on 2009-01-23
Great!

---

