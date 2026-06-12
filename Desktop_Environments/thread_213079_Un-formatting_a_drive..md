---
title: "Un-formatting a drive."
date: 2006-07-10
forum: Desktop Environments
---

### Post by xm1014 on 2006-07-10
Alrighty.

I have two hard drives.
The first one is an XP drive that uses NTFS.
the second one WAS NTFS. Now its a corrupted-ish ext2 drive.

How it happened:
I was installing Dapper Drake and I used the GParted tool in the install wizard. Everything looked great when I went to make changes, I was only going to shave off 20 gigs for the linux install and leave the rest for Storage. I click next and it "formats" it. Or so I thought. It goes to install and it cant find the partition i just made. ](*,) ](*,) ](*,) ](*,) 

So I go back to windows, thinking, ok it really didnt do anything. And my drive is now gone. Nothing recognizes it. I used a windows ext2-file-system reading tool and it sees it, but its corrupt. Is there any way i can UN-Format this drive?

---

### Post by az on 2006-07-10
You can recover some of the files that were once on that partition.

[http://ubuntuforums.org/showthread.php?t=204306&highlight=foremost](http://ubuntuforums.org/showthread.php?t=204306&highlight=foremost)

You can resize the partition (but not the filesystem!) again so that it occupies the whole space again beforehand.

To be safe (and if you have the room) image the entire drive using dd and work on that image.

---

