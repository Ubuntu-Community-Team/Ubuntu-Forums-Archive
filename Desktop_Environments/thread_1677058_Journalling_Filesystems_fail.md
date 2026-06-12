---
title: "Journalling Filesystems fail ??"
date: 2011-01-28
forum: Desktop Environments
---

### Post by dennisfisch on 2011-01-28
Hey there, I'd like to first introduce myself to the community. I'm already a long-time Linux user and have stuck with Ubuntu for the last 2 years after trying out various other distro's such as openSuSe and Mint (which is really just another Ubuntu flavour). I first made contact with Linux as part of the modules I had to take to get my CS degrees (currently have 2) and it just stuck with me. I even managed to convert my parents to Ubuntu.

Anyway, this post is about the fact that every time the system needs to check the partitions for errors during its boot-sequence, a full scan is always performed in favour of restoring the journal. From what I've learned in Uni, the file-system is keeping a journal of activity that helps speed up the process of cleaning after a crash. I only use journalling file-systems:
SDB2 ext4 at /
SDB6 ext3 at /home
SDB7 ext3 at /srv/music
SDA1 ext3 at /srv

It doesn't particularly help that there is no further information or progress update when discs are checked during boot-up. I couldn't even SSH into my machine. 

All partitions mount perfectly fine when cancelling the process, which I usually do, since sitting in front of a status message which doesn't tell me how long I am supposed to wait gets old really fast.

How is that even though I only use journalling file-systems, it still performs full-partition scans? I realise that there are conditions for which this is inevitable, but this seems to happen every single time for me.

Thanks very much in advance and especially if you kept up reading the entire post (sorry for the long post).

---

### Post by ajgreeny on 2011-01-28
It certainly should not happen every time you boot the machine and as it is, it points to some sort of file system problem.

Have a look at the output of the command sudo tune2fs /dev/sdx#, where the sdx# is youe ubuntu OS partition.  Towards  the bottom of the output will be a few lines telling you the info that I am intertested in, ie:-
```
Mount count:              4
Maximum mount count:      70
Last checked:             Wed Jan 26 13:50:26 2011
Check interval:           15552000 (6 months)
Next check after:         Mon Jul 25 14:50:26 2011
```Let's see that and then figure out where we go from here.

---

### Post by dennisfisch on 2011-01-28
Thanks for your response, I think you forgot to include the -l parameter as tune2fs just outputs its usage info otherwise ;)
Anyway, here you go:

```
dfisch@dfisch-desktop:~$ sudo tune2fs -l /dev/sdb2
tune2fs 1.41.12 (17-May-2010)
Filesystem volume name:   Ubuntu 10.04
Last mounted on:          /
Filesystem UUID:          f1ea94cf-c45e-43da-a070-547ce8fca30d
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              1281120
Block count:              5120687
Reserved block count:     256034
Free blocks:              3090821
Free inodes:              917733
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1022
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8160
Inode blocks per group:   510
Flex block group size:    16
Filesystem created:       Fri Apr  2 18:51:07 2010
Last mount time:          Fri Jan 28 11:06:30 2011
Last write time:          Fri Jan 28 11:06:18 2011
Mount count:              1
Maximum mount count:      25
Last checked:             Fri Jan 28 11:06:18 2011
Check interval:           15552000 (6 months)
Next check after:         Wed Jul 27 12:06:18 2011
Lifetime writes:          77 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
First orphan inode:       1047620
Default directory hash:   half_md4
Directory Hash Seed:      c169e0d4-ba75-4ffa-8d19-51faee0cca3d
Journal backup:           inode blocks

```

I went and issued the command for every ext partition and they all come back clean... weird, ain't it?
I'm not auto-mounting any NTFS partitions, nor is any mass-storage device connected to the pc.

---

### Post by ajgreeny on 2011-01-28
Whoops, sorry about the missing -l.

However, as you say, your output looks absolutely correct, though I think the Maximum mount count used to be 30, but has now changed to 25; I have no idea why.

Perhaps it would be worth running e2fsck from a live CD on each ext# partition to see if that does a better job than the boot time check; it sometimes can, though again, I've never understood why.  So boot the live CD/USB and run ```
sudo e2fsck /dev/sdx#
``` for each partition.

---

### Post by Claus7 on 2011-01-28
Hello,

> **ajgreeny said:**
> 
Perhaps it would be worth running e2fsck from a live CD on each ext# partition to see if that does a better job than the boot time check; it sometimes can, though again, I've never understood why.  So boot the live CD/USB and run ```
sudo e2fsck /dev/sdx#
``` for each partition.

Just to point out that this command should be executed while the partition is unmounted (mind!).

Regards!

---

### Post by psusi on 2011-01-28
Does this happen after every clean reboot, or only once in a while?  The journal is used to recover quickly after a crash, but by default, a full check is forced after so many mounts or so much time has passed just to be sure everything is ok.  Imho, this is an unnecessary waste of time and you can turn it off with tune2fs.

---

### Post by ajgreeny on 2011-01-28
From his tune2fs output the OP's system is set to check every 25 boots by default; too close an interval in my opinion, mine being set to 70, without problems arising, but the OP's system is obviously faulty in some way, as it seems to be checking at every boot.

---

### Post by dennisfisch on 2011-01-28
> **psusi said:**
> Does this happen after every clean reboot, or only once in a while?  The journal is used to recover quickly after a crash, but by default, a full check is forced after so many mounts or so much time has passed just to be sure everything is ok.  Imho, this is an unnecessary waste of time and you can turn it off with tune2fs.

This exactly... seems like something left over from a beta phase. Do you have any idea how to turn this off permanently? I'm not on the machine right now, posting from my android phone :) 
I'll check this out tomorrow

---

