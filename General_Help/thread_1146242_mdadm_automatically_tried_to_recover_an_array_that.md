---
title: "mdadm automatically tried to recover an array that doesn't exist and killed my data"
date: 2009-05-02
forum: General Help
---

### Post by J3anyus on 2009-05-02
This morning I flashed the BIOS on my motherboard because it was really out of date and I wanted to see if it might help with some random issues I was having.  I have a software RAID 5 in mdadm that's made up of three 320GB drives, and I knew that flashing my BIOS might confuse mdadm as to the ordering of the drives and that I might have to reconfigure my RAID setup.

After flashing the BIOS, I rebooted, and I got an mdadm error when assembling /dev/md0, as expected.  I did cat /proc/mdstat just to see what it was doing, and it showed a RAID 1 device that it had assembled between two of my 320GB drives.  And the worst part - it was trying to recover this array! Note that I've always had a RAID 5 setup, so I have no idea why it found a RAID 1 array or why it started automatically recovering it...I'd expect a recover operation would have to be initiated by the user, but apparently not.

Anyway, I ran mdadm --stop /dev/md0 as fast as I could, although the recovery operation was already at about 0.9% at that point.  I then assembled the RAID 5 array manually with mdadm --assemble, and it came together just fine.  When I try to mount it though, I get an ext3 error:

EXT3-fs error (device md0): ext3_check_descriptors: Block bitmap for group 3968 not in group (block 0)!
EXT3-fs: group descriptors corrupted!

I realize that I'm pretty screwed right now, but I'm hoping that there's some chance of recovering the majority of my data since mdadm only overwrote 0.9% of two drives.  I'm considering trying to run a recovery on my RAID 5 array, but don't want to do that yet as I'm concerned that it might make things even worse.

Any suggestions for what I can do from here?  I'm a little freaked out because I've trusted my data to mdadm for quite awhile and have about 8 years of data on there that I really don't want to lose.

Thanks!

---

### Post by fjgaude on 2009-05-02
Well, from my experience and knowledge, BIOSs, CPUs, motherboards have nothing to do with how **mdadm** assembes an array. It uses the UUID of the array, which is the same as each drive in the array, that was written on first --create. It doesn't use the names of drives or what slots they may be in. This UUID is not the one used to mount a drive or an array.

So, something is amess here.

Can you think of anything you might have done other than upgrade the BIOS?

---

### Post by J3anyus on 2009-05-02
I don't really know why it happened, but at this point, it doesn't matter.  The volume is corrupted and I need to do what I can to try to recover data from it.  I'm dd'ing the assembled (but broken) RAID 5 array to an external drive right now and then I'm going to run an fsck.  If that doesn't help, I'm not sure what to do, and that's where I'm looking for suggestions.  I know that there are several pieces of software out there that claim to recover data from broken ext3 volumes - any ideas for which ones would be the best?

---

### Post by fjgaude on 2009-05-02
You there are at least two such programs that aid in getting data back, but I simply can't remember their names. If you do a google you get this:

[http://search.yahoo.com/search?p=linux+data+recovery+software&ei=UTF-8&fr=ubuntu](http://search.yahoo.com/search?p=linux+data+recovery+software&ei=UTF-8&fr=ubuntu)

You might go through all this and find something that is free!

Good luck!

---

### Post by J3anyus on 2009-05-04
Just as a follow-up for anyone who finds this thread later, I was able to recover a significant amount of my data.  Here's the exact process I used (note that everything done here must be run from a root shell):

* Booted from a Xubuntu Live CD and assembled my RAID:
```
apt-get install mdadm
mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1
```
* Made a block-by-block copy of my array to a separate disk, so that if I blew it up during the recovery I would still have another copy of it.  Note that this is with GNU ddrescue, which is not the same as Kurt's dd_rescue.  For my 640GB volume, this took about 6-7 hours.
```
ddrescue -r2 /dev/md0 /dev/sde1 /home/ubuntu/ddrescue.log
```
* Figured out where the backup copies of the ext3 superblock were located on the disk:
```
mkfs.ext3 -n /dev/sde1
```
* Ran fsck, manually specifying the location of the superblock and using -y so fsck would automatically assume sensible defaults without asking me first.  This took about 10-12 hours, with the majority of the time spent cloning multiply-claimed blocks.  The number after -b is the location of the superblock, as determined above.
```
fsck.ext3 -y -b 12345678 /dev/sde1
```
* Mounted the filesystem and took a look in lost+found:
```
mount /dev/sde1 /mnt
cd lost+found
```

Although the original directory names were lost, the majority of the filenames and subdirectory names were still intact.  All in all, I was able to recover about 90% of my data, which is fantastic considering I wasn't expecting to get any of it back.

---

### Post by fjgaude on 2009-05-04
Great, and thanks for thinking of others.
'grok'

---

