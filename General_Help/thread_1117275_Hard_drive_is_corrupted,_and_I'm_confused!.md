---
title: "Hard drive is corrupted, and I'm confused!"
date: 2009-04-05
forum: General Help
---

### Post by Fixman on 2009-04-05
Today, when booting my Ubuntu machine, I found a surprise: since it was a "filesystem with errors", it would forcely fsck it, and fsck would fail. No problem, I just booted into my old Parted Magic CD, fsck the filesystem, and problem solved. This was the output:

```

root@PartedMagic:~# fsck -vy /dev/sda1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 8617988 has zero dtime.  Fix? yes                                

Inodes that were part of a corrupted orphan linked list found.  Fix? yes

Inode 8617989 was part of the orphaned inode list.  FIXED.
Inode 8617990 was part of the orphaned inode list.  FIXED.
Inode 8617991 was part of the orphaned inode list.  FIXED.
Inode 8617992 was part of the orphaned inode list.  FIXED.
Inode 8618009 was part of the orphaned inode list.  FIXED.
Pass 2: Checking directory structure                                           
Entry '%gconf.xml' in /home/martin/.gconf/desktop/gnome/applications/window_manager (2547760) has deleted/unused inode 2548831.  Clear? yes

Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts                                              
Pass 5: Checking group summary information                                     
Block bitmap differences:  -(10200818--10200820) +(10212179--10212180)         
Fix? yes

Free blocks count wrong for group #311 (142, counted=143).                     
Fix? yes

Free blocks count wrong (9428293, counted=9428294).
Fix? yes

Inode bitmap differences:  -2548624 -(8617988--8617992) -8618009
Fix? yes

Free inodes count wrong for group #311 (6530, counted=6531).                   
Fix? yes

Free inodes count wrong for group #1052 (8109, counted=8115).
Fix? yes

Free inodes count wrong (9363141, counted=9363148).
Fix? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

  221492 inodes used (2.31%)
    2589 non-contiguous files (1.2%)
     299 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 17791/1140/4
28886723 blocks used (75.39%)
       0 bad blocks
       6 large files

  178174 regular files
   21251 directories
      69 character device files
      26 block device files
       3 fifos
     471 links
   21946 symbolic links (20752 fast symbolic links)
      14 sockets
--------
  221954 files

```

If I wanted to fsck again, it would tell me the filesystem is clean. However, when I boot, for some reason it mounts my filesystem as readonly and so I only get a mouse and a brown (ubuntu brown) background. Anybody has any other way to solve this?

---

### Post by Sam Lars on 2009-04-07
When the filesystem encounters errors it remounts the drive as read-only.  You could have problems with your drive if the fsck says it's clean.

---

### Post by Bucic on 2011-09-16
Under installed ubuntu:
```

sudo fsck -nvf /dev/sda1
[sudo] password for *****: 
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
Warning!  /dev/sda1 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix? no

Inode 266956 was part of the orphaned inode list.  IGNORED.
Inode 275724 was part of the orphaned inode list.  IGNORED.
Inode 275799 was part of the orphaned inode list.  IGNORED.
Inode 276378 was part of the orphaned inode list.  IGNORED.
Inode 276479 was part of the orphaned inode list.  IGNORED.
Deleted inode 299533 has zero dtime.  Fix? no

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -(930311--930312) -(930323--930324) -930337 -930339 -930341 -(1860637--1860638)
Fix? no

Free blocks count wrong for group #28 (11149, counted=11148).
Fix? no

Free blocks count wrong (1117529, counted=1117517).
Fix? no

Inode bitmap differences:  -266956 -275724 -275799 -276378 -276479 -299533
Fix? no

Free inodes count wrong for group #32 (1, counted=0).
Fix? no

Free inodes count wrong for group #33 (1, counted=2).
Fix? no

Free inodes count wrong (361133, counted=361108).
Fix? no


/dev/sda1: ********** WARNING: Filesystem still has errors **********


  228691 inodes used (38.77%)
     147 non-contiguous files (0.1%)
     303 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 192356/62
 1241767 blocks used (52.63%)
       0 bad blocks
       1 large file

  154571 regular files
   27434 directories
      59 character device files
      26 block device files
       0 fifos
     394 links
   46587 symbolic links (36173 fast symbolic links)
      24 sockets



```

How can I verify if my system is OK? When issue
```

e2fsck /dev/sda2

```
on PartedMagic LiveUSB (latest) it returns "clean".

---

### Post by haqking on 2011-09-16
Have you tried doing a unmounted fsck ?

make sure you have a backup of all data and then drop to runlevel 1 or to a live CD and run a fsck when the drives are unmounted

---

### Post by Bucic on 2011-09-16
The partition was UNmounted. 

Anyway, GSmartControl claims 3 of my disk parameters deserve "pre-failure" flag and it's an ooooold notebook so it might be something to it. Then I found this [**Idea #6972: Ubuntu needs a tool for marking bad sectors of harddrives**]("http://brainstorm.ubuntu.com/idea/6972") and [**Tips4Linux.com - Scan for bad sectors in Linux**]("http://tips4linux.com/scan-for-bad-sectors-in-linux/")

In the meantime I'll try to run e2fsck with c or -cc parameter. And prepare to replace that $100 notebook with a contemporary $300 one...

---

### Post by haqking on 2011-09-16
> **Bucic said:**
> The partition was UNmounted. 

Anyway, GSmartControl claims 3 of my disk parameters deserve "pre-failure" flag and it's an ooooold notebook so it might be something to it. Then I found this [**Idea #6972: Ubuntu needs a tool for marking bad sectors of harddrives**]("http://brainstorm.ubuntu.com/idea/6972")

In the meantime I'll try to run e2fsck with c or -cc parameter. And prepare to replace that $100 notebook with a contemporary $300 one...

The output you posted said mounted

---

### Post by Bucic on 2011-09-16
> **haqking said:**
> The output you posted said mounted
The output comes from installed ubuntu. The *fsck operations were performed under PartedMagic LiveUSB.

---

### Post by walt.smith1960 on 2011-09-16
> **Bucic said:**
> The partition was UNmounted. 

Anyway, GSmartControl claims 3 of my disk parameters deserve "pre-failure" flag and it's an ooooold notebook so it might be something to it. Then I found this [**Idea #6972: Ubuntu needs a tool for marking bad sectors of harddrives**]("http://brainstorm.ubuntu.com/idea/6972") and [**Tips4Linux.com - Scan for bad sectors in Linux**]("http://tips4linux.com/scan-for-bad-sectors-in-linux/")

In the meantime I'll try to run e2fsck with c or -cc parameter. And prepare to replace that $100 notebook with a contemporary $300 one...

Would the rest of the machine be worth a new hard drive?  Of course, it could have a drive **controller** or motherboard problem instead of a disk problem. I had a similar problem some time ago and bought a new hard drive.  The problem was not with the drive so I bought an inexpensive drive enclosure, put the good hard drive in it and now have another external hard drive.

---

### Post by Bucic on 2011-09-16
> **walt.smith1960 said:**
> Would the rest of the machine be worth a new hard drive?  Of course, it could have a drive **controller** or motherboard problem instead of a disk problem. I had a similar problem some time ago and bought a new hard drive.  The problem was not with the drive so I bought an inexpensive drive enclosure, put the good hard drive in it and now have another external hard drive.
I have already encountered **false bad sector warning in linux** Disk Tool so I wouldn't be surprised if GSmartControl also indicates falsely while the ubuntu reported errors are 'just some errors'. Long story short it's more probable that linux tools for disk condition analysis suck than malfunction of my disk. Like a 10 to 1.

I did *$ sudo fsck -pcfv /dev/sda1 * and that [http://tips4linux.com/scan-for-bad-sectors-in-linux/](http://tips4linux.com/scan-for-bad-sectors-in-linux/) and no errors were reported. The output of sudo fsck -nvf /dev/sda1 under Ubuntu looks same as before.

---

### Post by Bucic on 2011-09-17
I was right. The diagnostic tool (GSmartControl) is horse * ! I've diagnosed a healthy, relatively new drive and and Gsmart showed me almost exactly same looking set of results! That's a second linux disk tool that falsely claims drives are in poor condition!

---

