---
title: "Continuing to adjust partitions"
date: 2006-04-30
forum: Desktop Environments
---

### Post by Rhapsody on 2006-04-30
Now I have Kubuntu installed, and I'm pretty satisfied with it. The only proble is the Houdini (my second HD) has a rather large NTFS partition on it with a lot of a data I'd like to keep around for usage with Kubuntu. But I'll need to be doing some serious read/write operations to that data (it's my main drive for torrents) so it's not really practical to leave it as NTFS.

I do have a plan though. While Linux may not be reliable for writing to an NTFS drive, I gather that it is reasonably reliable for reading from NTFS partitions. Also, I know that it is possible to carve additional partitions out of NTFS partitions (I've already done this for my swap partition), the data on the partition takes less than 90GB of a 248GB partition, and the last thing I did with the NTFS partition was to defragment it (placing all of the data at the start of the partition). Hence, my five-step plan goes as follows:

Step 1: Use the spare space on the NTFS partition to create an ext3 partition inbetween the NTFS and swap partitions large enough to store all of the data on the NTFS partition.
Step 2: Copy all data on the NTFS partition to the new ext3 partition.
Step 3: Delete NTFS partition and use new space to create a second ext3 partition (placed before the first ext3 partition).
Step 4: Copy data on the ext3 partition partition I created earlier to the ext3 partition at the start of the drive.
Step 5: Delete ext3 partition I created first and expand the other ext3 partition to fill the new space.

As far as I can tell, this plan looks sound and should leave me with an ext3 partition with all the data my NTFS partition currently contains.

I'm not sure how I should go about putting my plan into action though. The last time I partitioned this drive was while installing Kubuntu (which really wasn't all that long ago) but I don't know how to change my partitions about now that it's installed.

So how exactly do I change my partitions around now that Kubuntu's installed and running?

---

### Post by olsonar on 2006-04-30
install gparted. It's fairly easy to use, you shouldn't have any trouble with it. also, don't bother with steps 4 and 5, just expand the ext3 partition you copied the data to.

---

### Post by Rhapsody on 2006-04-30
[QUOTE=olsonar]install gparted. It's fairly easy to use, you shouldn't have any trouble with it.[/QUOTE]
Where do I get that from?

[QUOTE=olsonar]also, don't bother with steps 4 and 5, just expand the ext3 partition you copied the data to.[/QUOTE]
How can I do that? The free space will go before the ext3 partition, I thought I could only expand a partition into free space that came after the partition?

---

### Post by breezyfox on 2006-05-01
you can also use live cd to reduce the ntfs partition.
install ububtu and then copy all your ntfs docs to ext part. 
You may think then converting ntfs part. to fat32 as it is more easy to RW.
extend your present partition of ext. etc.etc.
these are some of the many options you can try or plan.

hope this gives you some more ideas.
bz

---

### Post by [S|G] on 2006-05-01
Alternatively you might want to use EXT2IFS, which is a tool that allows windows to read and write data to EXT2 and EXT3 partitions. The url for their site is [http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htmDownload](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htmDownload)

Although ubuntu does read NTFS problems with no risk of corrupting your data :)

---

### Post by olsonar on 2006-05-01
Install gparted using this command:

```
sudo apt-get install gparted
```

And yes, gparted can expand backwards.

---

### Post by nejode on 2006-05-01
You just have to resize the ntfs partition and make a fat32 partition that's RW for windows and linux. Go to this page> [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page), download and burn the iso, boot from it, and you will have QTParted, GNU Parted and many useful Linux tool (+documentation) and how to's.  If you are familiar with windows tools, go to this page> [http://www.9down.com/downloads.php?fileid=207](http://www.9down.com/downloads.php?fileid=207), download the Hiren's boot CD iso, it has plenty partitioning tools (and what you need is a windows partition!)

---

### Post by Rhapsody on 2006-05-01
nejode & breezyfox: I don't see much reason to keep using FAT32. I fully intend to remove Windows from my PC in the forseeable future. Access from within Windows is therefore a non-issue for me.

olsonar: Well, I have GParted now, but the only options available when I unmount my NTFS partition are to delete it (not really what I wanted) or to convert it to various other filesystems. Is it really going to be that easy?

---

### Post by olsonar on 2006-05-01
Oops. I forgot. You heed to install ntfsprogs for gparted to properly support ntfs. Just:

```
sudo apt-get install ntfsprogs
```

Now you'll be able to resize the NTFS partition.

---

### Post by Rhapsody on 2006-05-01
Ah yes, a bit more of a problem. This partition is on the same disk as my swap partition, and I'll need to unmount that before I make any changes. I've got 512MB RAM on this system, am I going to run into problems?

---

### Post by olsonar on 2006-05-01
512MB should be enough. Just don't try to run anything else at the same time as the partitioner. To be certain it'll work, goto System -> Administration -> System Monitor,  and click the resources tab. It'll tell you how much of your RAM is being used. I have 1GB RAM and typically it's about 200 - 300 MB used.

---

### Post by nejode on 2006-05-01
If you use the SysRescue CD you don't need to unmount anything because you're booting from the CD and your file systems won't be auto-mounted  by your /etc/fstab.  Questions: how big is your first HDD?... can it hold at least part of those 90 gb of data and burn the rest into a few DVD's?... External HDD?  With all the data in a safe place you'll be free to play at will with Houdini.

---

