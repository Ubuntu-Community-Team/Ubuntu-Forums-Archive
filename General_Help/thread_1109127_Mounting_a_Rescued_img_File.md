---
title: "Mounting a Rescued img File"
date: 2009-03-28
forum: General Help
---

### Post by icarusfall on 2009-03-28
Hello! I have had a hard drive break on me (I use Ubuntu 8.10, by the way). Fsck didn't seem to be fixing anything, so I resorted to dd_rescue, or rather dd_rhelp, which is a shell script that uses dd_rescue. Basically I followed the instructions here:
[http://www.debianadmin.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html](http://www.debianadmin.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html)

I did dd_rhelp on the hard drive to create an image file backup.img.

The filesystem in the image file presumably had errors (I left dd_rhelp running for three days, and quit it after those three days), so I ran fsck on it. The image file, by the way, is 153gig, so it looks like a fair amount of the drive was rescued.

Anyway, so I ran:
```
charlie@woobuntu:/media/disk-1$ sudo fsck /media/disk-1/backup.img
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
The filesystem size (according to the superblock) is 40335190 blocks
The physical size of the device is 40305154 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

/media/disk-1/backup.img contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/media/disk-1/backup.img: 54/20168704 files (0.0% non-contiguous), 648197/40335190 blocks
```


The first time I ran it, there were a lot of short reads, but I got through that, and now whenever I run it, I get the above output. Does that look OK? Is the 54/20168704 files thing a problem? Is 54 a bit low?

Anyway, I now try to mount the image file but I get an error:
```
charlie@woobuntu:/media$ sudo mount /media/disk-1/backup.img /media/temp
mount: /media/disk-1/backup.img is not a block device (maybe try `-o loop'?)
```

So I tried:
```
charlie@woobuntu:/media/disk-1$ sudo mount -o loop /media/disk-1/backup.img /media/Pfiles

```

But now I browse to /media/Pfiles and there's nothing there besides the lost+found folder. When I go into this (and I have to change to root to go into this) there are only 43 small files, amounting to about 180.2k, and I don't recognise any of them.

Am I doing anything wrong? Or is my data lost forever? It's my own stupid fault for not backing up my data regularly, but I really would hate to lose it all.

Thanks for any help that anyone can provide.

Charlie

---

### Post by dcstar on 2009-03-28
> **icarusfall said:**
> Hello! I have had a hard drive break on me (I use Ubuntu 8.10, by the way). Fsck didn't seem to be fixing anything, so I resorted to dd_rescue, or rather dd_rhelp, which is a shell script that uses dd_rescue. Basically I followed the instructions here:
[http://www.debianadmin.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html](http://www.debianadmin.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html)

I did dd_rhelp on the hard drive to create an image file backup.img.

The filesystem in the image file presumably had errors (I left dd_rhelp running for three days, **and quit it after those three days**), so I ran fsck on it. The image file, by the way, is 153gig, so it looks like a fair amount of the drive was rescued.
.........
Am I doing anything wrong? Or is my data lost forever? It's my own stupid fault for not backing up my data regularly, but I really would hate to lose it all.

Thanks for any help that anyone can provide.

Charlie

Firstly, you should have let it run until completion as there is no guarantee that you have all the critical data from the drive.

Secondly, this tool is for backing up individual partitions, did you use it that way?

---

### Post by icarusfall on 2009-03-29
Thanks for the reply. Yes, I was using it to back up the first partition (my old /home partition) on the hard drive. To be honest, I just want to rescue my photos, I don't really care about any of the rest of the stuff.

Should I really have let it run to completion? I was under the impression it can take months to do that...I thought the advantage of dd_rhelp is that it prioritises the least damaged blocks so that the lion's share of the data recovery would be done early on.

My other alternative is to use photorec, from the testdisk package. Do you have any advice? I'm happy to start up dd_rhelp again (the log files are still there, so it should just carry on from where it left off). Alternatively I could try photorec.

What do you reckon?

---

### Post by icarusfall on 2009-03-29
Also, although it says that the backup.img file is 153gig in file properties, when I go to System Monitor, it says that the drive I'm backing the file up to (which is otherwise empty) only has 1.7gig used, so perhaps it hasn't backed up as much as I'd thought...

---

### Post by icarusfall on 2009-03-29
Something I'm also trying is to run fsck, but it seems to be taking absolutely ages (again, in the order of days), but it doesn't actually crash. Am I better off just leaving fsck running? I've used testdisk to find all the backup superblocks on the partition, so I could try running fsck and specifying the -b and -B options as suggested here:
[http://www.cgsecurity.org/wiki/Advanced_Find_EXT2_EXT3_Backup_SuperBlock](http://www.cgsecurity.org/wiki/Advanced_Find_EXT2_EXT3_Backup_SuperBlock)

Again, I'd be grateful for any advice at all.

Thanks

Charlie

---

### Post by icarusfall on 2009-03-29
By the way, I know this will seem obvious to everyone, but I was getting a lot of strange errors booting up into Ubuntu (eg bad EIP value, UDEVD tainted) for many weeks leading up to the hard drive's death. Like an idiot, I didn't connect them to any error on the hard drive. If anyone else reads this, and they're getting strange errors such as this, my advice would be to backup all the data on your computer.

Obviously it's a good idea to back up all your data anyway, but for some reason I assumed I'd be immune...

---

