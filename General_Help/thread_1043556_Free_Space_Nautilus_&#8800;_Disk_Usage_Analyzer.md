---
title: "Free Space: Nautilus &#8800; Disk Usage Analyzer"
date: 2009-01-18
forum: General Help
---

### Post by vegetarianshrimp on 2009-01-18
When I open nautilus, it says at the bottom that there is 9.9 GB of free space on my hard drive. When I open Disk Usage Analyzer, it says there is 10.6 GB of free space. 

Which is right?

How can I make them say the same thing?

---

### Post by steeleyuk on 2009-01-18
Same problem. No idea why though some people have reported this on Launchpad.

I'd take Nautilus as being right to be honest, I've added it up across three disks and Nautilus seems to be the one reporting it correctly.

You can see what the command line says by typing:

df -h

---

### Post by unutbu on 2009-01-18
Disk Usage Analyzer (baobab) gives "incorrect" results when run as a normal user. In particular, it does not report the space used by files that the normal user can not read. These include some files owned by root. 

I believe if you have a partition/directory shared via samba, that space is also reported by baobab (as part of ~/.gvfs). This further complicates things, because the size stats will no longer be directly comparable with the output of "df -h".

To see the difference, try running baobab as root:
```

gksu baobab
```
or click System>Pref>Main menu and change the command for Disk Usage Analyzer to "gksu baobab".

---

### Post by jgoguen on 2009-01-18
I don't know if this is the reason, but it could be that one is reporting the sum of the actual size on disk of each file, and the other is reporting the total size reserved.  Basically, each file is split into blocks.  If the end of a file doesn't use the whole block, that space is unused (so not counted towards the file's total size) but it's not available for other files to make use of.  If I'm right, Nautilus is using the sum of the size of each file on disk, while Disk Usage Analyzer is using the total size reserved for files.  If I'm right of course, there could be something else :)

---

### Post by steeleyuk on 2009-01-18
Running as root says the same as running as standard user for me.

This [post on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/baobab/+bug/244086") might explain it:

> On my system, df and Nautilus agree with regards to free space:
Total: 226.4 GiB ; 243.0 GB
Used: 199.2 GiB ; 213.9 GB
Free: 15.7 GiB ; 16.9 GB

Baobab says:
Total: 226.4 GB
Used: 199.2 GB
Free: 27.2 GB

If about 5% of my disk is reserved, that explains the discrepancy:
(226.4 * 0.05) + 15.7 = 27.0

There is no option to disable gvfs in the preferences of the current Baobab, so I cannot test that aspect of the bug.

---

### Post by vegetarianshrimp on 2009-01-18
Thanks everyone for replying, I think I understand now:
DUA is right, but Nautilus is the one telling me how much space I can use for files and such.
Am i right?

p.s. Is there a command to take all the reserved space for files and give it back to the hard drive?

---

### Post by jgoguen on 2009-01-18
> **vegetarianshrimp said:**
> Thanks everyone for replying, I think I understand now:
DUA is right, but Nautilus is the one telling me how much space I can use for files and such.
Am i right?
In a way, they're both right, depending on how you look at "how much space do I have used".  I've never compared them, but from what you're reporting I would consider Nautilus (reporting 9.9GB free) as correct for how much space is available (size_of_drive - 9.9GB = amount of space used or reserved for files), and Disk Usage Analyzer as correct for how much data is actually stored on the drive (size_of_drive - 10.6GB = amount of data actually stored).

> **vegetarianshrimp said:**
> p.s. Is there a command to take all the reserved space for files and give it back to the hard drive?
I don't believe so.  If extents are used, then it may be possible (but I doubt it) but if not then there's no way.  If a block is (for example) 512kB, and *myfile* only needs 126kB of that block, there's no way to tell the system to allow the remaining space to be used for another file.  The excess 386kB will remain reserved for *myfile* to use when it grows.  I have a quick and dirty C program that will recursively traverse a directory and report both the file size and the amount of space actually reserved for the file if you're interested in seeing the difference on a per-file basis.  The difference between Nautilus and Disk Usage Analyzer shows you the overall difference between them.

---

### Post by vegetarianshrimp on 2009-01-18
> **jgoguen said:**
>   I have a quick and dirty C program that will recursively traverse a directory and report both the file size and the amount of space actually reserved for the file if you're interested in seeing the difference on a per-file basis.

That sounds interesting. Where do I download it?

---

### Post by unutbu on 2009-01-18
vegietarianshrimp, there is a way to modify the amount of reserved space. 
The command:
```

sudo tune2fs -m1 /dev/sda3
```

will set the amount of reserved space on /dev/sda3 to equal 1% of the total space available. If you change the command to
```

sudo tune2fs -m0 /dev/sda3
```

you can remove the reserved space completely. However, you should not do that if /dev/sda3 is your root Linux partition. The operating system writes to files in /var/log when you boot, and as you work. If the partition containing /var/log were to fill up completely, then you would no longer be able to boot. To prevent this from happening, the filesystem reserves some hard disk space that only root can use. So you as a normal user will think the disk is full before the operating system thinks the disk is full. This allows you to fix the problem before the operating system becomes totally inoperable. 

How much reserved space you need is up to you. I think the 5% default was set back in the days when a 10GB hard drive was considered large. That would have given you 500MB of reserved space. Nowadays, with 1TB drives, 5% reserved space is ridiculously large. 

By the way, if you want to specify the reserved space in blocks, you can use:
```

sudo tune2fs -r51207 /dev/sda3
```

This reserves 51207 4K-blocks = 204828 KiB ~ 200 MiB
(4 KiB = one 4K-block)

Finally, to find the device name (e.g. /dev/sda3) for your partitions, you
can look in the output of 
```

df
```

or 
```

sudo fdisk -l
```

---

### Post by vegetarianshrimp on 2009-01-18
thanks unutbu. For a newbie, which one of these options would be the safest and will save the most disk space?

---

### Post by jgoguen on 2009-01-18
> **vegetarianshrimp said:**
> That sounds interesting. Where do I download it?
It's attached to this post.  I'll assume you download it to your home directory.  Open a terminal (Applications -> Accessories -> Terminal) and enter these commands:
```
tar zxf dirscan.tar.gz
cd dirscan
make Ass4Q3
./bin/dirscan /path/to/report/
```
You will need the **build-essential** package installed (**sudo aptitude install build-essential**) for this to work.  I make no promises that this works 100% perfectly.  It was thrown together in about 15 minutes for a class, and it worked fine on the various directories I tested it with, but that makes no guarantee that it will work perfectly on every directory.  It will report the directory you give it and all sub-directories.  There's no option to turn this off.

---

### Post by vegetarianshrimp on 2009-01-18
> **jgoguen said:**
> It's attached to this post.  I'll assume you download it to your home directory.  Open a terminal (Applications -> Accessories -> Terminal) and enter these commands:
```
tar zxf dirscan.tar.gz
cd dirscan
make Ass4Q3
./bin/dirscan /path/to/report/
```You will need the **build-essential** package installed (**sudo aptitude install build-essential**) for this to work.  I make no promises that this works 100% perfectly.  It was thrown together in about 15 minutes for a class, and it worked fine on the various directories I tested it with, but that makes no guarantee that it will work perfectly on every directory.  It will report the directory you give it and all sub-directories.  There's no option to turn this off.

Before I do this, how do I uninstall it afterwards?

---

### Post by jgoguen on 2009-01-18
> **vegetarianshrimp said:**
> Before I do this, how do I uninstall it afterwards?
Remove the *dirscan* directory that gets created when you unpack the file you download.  The Makefile has a lot more in it than just for this (it's the Makefile for everything I did in C for one class) but the Ass4Q3 target is for this file set.  You can review the target (and any other targets) to verify that it doesn't write outside the *dirscan* directory.

---

### Post by unutbu on 2009-01-18
vegetarianshrimp, this is the command I use for my root Linux partition.
```

sudo tune2fs -r51207 /dev/sda3
```

Choosing 200MiB of reserved space was an arbitrary decision on my part -- I have no deep reasoning or sound defense for that number :)

Thanks jgoguen for dirscan program. I haven't been able to get the results to match up exactly yet, but in spirit, I think it reports the same type of info as
```

du -B1 --apparent-size DIR    # size of DIR in bytes
du -B1 DIR                    # disk space used in bytes
```

Using "-B1024" will report the results in KiB.

---

### Post by jgoguen on 2009-01-18
It's possible that I'm doing it wrong.  I'm assuming a 512kB block size because that's what we were told to do.  It's entirely possible that's wrong and we were told to do that to standardize results across multiple platforms.  If you start adding up the differences between size of data stored and size of space reserved, it adds up pretty quickly even assuming 512kB blocks.

---

