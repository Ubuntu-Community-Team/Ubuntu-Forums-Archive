---
title: "Constant fsck"
date: 2006-07-17
forum: Desktop Environments
---

### Post by katzman on 2006-07-17
Hello;
I have dapper running on a older computer of mine that i use for storage and watching things. I don't leave it on all the time because of noise and energy waste. Very often after i shutdown (using the menu in xfce, or shutdown -h now) and restart later at least half the time it fsck my main storage partition, not the system one. It is fairly annoying as it really delays the startup. I have the fs (ext3) set to check every 75 mounts; but when it does on of the fsck it gives some number like 40 000 for the number of times mounted since last check.
Anyone have an idea as to what is causing this
Partitions are just ext3, no lvm.

---

### Post by ahaslam on 2006-07-17
try this(REPLACE hda1 with your partition if its different)
sudo tune2fs -l /dev/hda1
look for Maximum mount count. 
To Change to every 75th mount try:
sudo tune2fs -c 75 /dev/hda1
or use -i if you'd rather set it by time instead of mounts.

Tony.

Credits to 'woedend' who helped me with a similar problem.

---

### Post by katzman on 2006-07-17
> **Anthony Haslam said:**
> try this(REPLACE hda1 with your partition if its different)
sudo tune2fs -l /dev/hda1
look for Maximum mount count. 
To Change to every 75th mount try:
sudo tune2fs -c 75 /dev/hda1
or use -i if you'd rather set it by time instead of mounts.

Tony.

Credits to 'woedend' who helped me with a similar problem.

i ran the tune2fs -l and it appears that my setting of the 75 mount interval was aet as it should. but i noticed that it had these:
Last mounted on:          <not available>
Mount count:              1
Maximum mount count:      75
Last checked:             Fri Jul 17 13:16:07 2020
Check interval:           15552000 (6 months)
Next check after:         Wed Jan 13 12:16:07 2021


and here is the full output

tune2fs -l /dev/hdd1
tune2fs 1.38 (30-Jun-2005)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          75732f46-d9cd-0f70-5ef2-52dc330076af
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr dir_index filetype needs_recovery sparse_super
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              8863744
Block count:              17705630
Reserved block count:     708225
Free blocks:              809828
Free inodes:              8850893
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Sun Apr 23 01:38:10 2006
Last mount time:          Mon Jul 17 13:25:05 2006
Last write time:          Mon Jul 17 13:25:05 2006
Mount count:              1
Maximum mount count:      75
Last checked:             Fri Jul 17 13:16:07 2020
Check interval:           15552000 (6 months)
Next check after:         Wed Jan 13 12:16:07 2021
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      5fc5d3da-d461-dfb3-fddb-6674214712ba
Journal backup:           inode blocks

---

### Post by ahaslam on 2006-07-17
I think you'll need to set the check interval to 0, from 6 months. Hopefully it'll then go from the mount count.

Tony.

PS. I don't think your callenda is set correctly (or wasn't during last check), 2020?

With all that, I wouldn't blame it if it were a little confused & decided to run every time ;)

---

### Post by utnubu001 on 2006-07-17
> **Anthony Haslam said:**
> I think you'll need to set the check interval to 0 from 6 months. Hopefully it'll then go from the mount count.

Tony.


What??
6 months?

---

### Post by orb9220 on 2006-07-17
Well if you just want to stop dosfsck on startup you do so thru the fstab

/dev/hdd1   /media/hdd1     vfat    defaults,utf8,umask=007,gid=46 0       0

The last 0 use to be a 1 which I changed to a zero and no more dosfschk

---

### Post by katzman on 2006-07-17
hmm i didn't notice that bit; and the 6 months was not set by me; i'll change the time and see if that helps.

As well i do want it to fsck every 75 mounts so the fstab method won't work

---

### Post by katzman on 2006-07-22
Just wanted to add that that was the problem and it is all okay now

---

