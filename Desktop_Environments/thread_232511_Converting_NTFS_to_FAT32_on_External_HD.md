---
title: "Converting NTFS to FAT32 on External HD"
date: 2006-08-08
forum: Desktop Environments
---

### Post by PCalitrack on 2006-08-08
Anyone have any experience converting from NTFS to FAT32 on an external hard drive. I have a SimpleDrive External 160GB, and I would like to make it compatible with linux. Would QtPartEd be able to do such a thing? It seems that it usually won't reconize my external hard drive when I run it. Thanks.

---

### Post by hopstah on 2006-08-08
i am unaware of any way to convert the file system backwards from ntfs to fat32.  it's possible to go from fat16 to fat32, and from ext2 to ext3, but i'm pretty sure the only way to do this is to do a reformat of the drive.

i just did a similar thing to get my music library onto an ext3 partition instead of fat32 - i recently decided to do away with windows, and felt that this would be a good idea.

so, depending on how much empty space you have, i'll tell you how you can take care of this.  if your external hard drive is less than 50% full, you'll be ok. (edit:  if it's more than 50% full, get it less than 50% full)

using the ubuntu livecd and the gparted that comes along with it, you can shrink the existing ntfs partition so that it takes up less than half of the drive space.  then, create a new partition on the newly freed up space on the drive.  once this is all done (it will probably take a while depending on how much data you have on the drive), you can mount both the ntfs partition and the new partition, and run ```
rsync -aS [path to ntfs partition] [path to new partition]
```

let this finish doing it's stuff, and then format the ntfs partition into a fat32 partition (i forget what this command is).  once this is done, you want to re-copy all of the data from the partition you made earlier back onto the newly formatted fat32 partition. ```
rsync -aS [path to new partition] [path to newly formatted fat32 partition]
``` once this is done, go back into gparted through the install process, and delete the second partition, and resize the first partition to take up all of the disk again, and you should be all set!

---

### Post by PCalitrack on 2006-08-08
Just wanted to say thanks for you help in answering my question. I haven't tried it yet, but now I have a verry good idea of how to do what I want to do.

So if my NTFS formatted external hard drive is empty, then I can go into GPartEd and mount the external hard drive, then delete the partition on it and add a FAT32 partition. I hear that FAT32 can only work on 32GB partitions though? Maybe, I'll just make a lot of 32GB partitions since I have a 160GB HD.

Thanks again. I'll let you know how it goes once I am able to clean the drive.

---

### Post by hopstah on 2006-08-08
i had my 300gb formatted with fat32 and it worked just fine, except for handling my non-standard characters in filenames, like umlauts and stuff.  it displayed them as weird characters, but they all still worked perfectly.

edit:  i also had an 80gigger at fat32.  i read that there is a limit imposed in winxp which doesn't allow for formatting to sizes larger than 32gb, but the filesystem itself has a theoretical limit of 2 terabytes, so you'll be ok.

---

### Post by PCalitrack on 2006-08-09
Just wanted to report that GPartEd fits the bill. It was able to resize my external hard drive and then add a new FAT32 partition. My only complaint is that the Live CD refuses to reboot. Anyways, I am very satisfied. Thanks.

---

### Post by lefty.crupps on 2006-08-09
Depending on what is on the drive, it is possible to just delete all of the partitions and reformat the whole thing as Fat32 in GParted or QTParted, just basically starting over.

I have noticed, and I don't know why this is, when I make a Fat32 partition with Linux it doesn't seem to always work correctly.  I might copy files from a Win-created Fat32 partition to a Linux-created, new Fat32 partition, and I'll get Permission errors for some file.  Since both are Fat32 and therefor have no file permissions built into the Fat32 file system, I do not know why this is.  When I copy the same data using Windows, I do not get these errors.  Once the free space has been written to fully (and then cleared out / deleted) this error seems to disappear.

My suggestion, then: Repartition the whole thing in Fat32 in Linux.  Boot into Windows and fill it with files.  Delete these files, and now use your empty drive in both systems.

---

