---
title: "split flash drive fat16/ext2 problem"
date: 2009-02-01
forum: General Help
---

### Post by dragos240 on 2009-02-01
Okay so i partitioned my usb drive into 2, one for bringing things to my school (fat16) and one for home (ext2) but annoyingly, i can't see any of the files i placed inside, i pressed ctrl + H and nothing either. Any idea how to retreive these files. I know i put them inside there, and it says that i did. Also the file size says that there are things inside. Help?

---

### Post by dragos240 on 2009-02-02
> **dragos240 said:**
> Okay so i partitioned my usb drive into 2, one for bringing things to my school (fat16) and one for home (ext2) but annoyingly, i can't see any of the files i placed inside, i pressed ctrl + H and nothing either. Any idea how to retreive these files. I know i put them inside there, and it says that i did. Also the file size says that there are things inside. Help?

Bump?

---

### Post by Neural oD on 2009-02-02
as far as i know windows does not recognize partitioned flash drives. That being said ubuntu should. What does: "sudo fdisk -l" give you

---

### Post by dragos240 on 2009-02-02
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          67      538146   83  Linux
/dev/sdb2              68         124      457852+   6  FAT16

```

And wouldn't windows the fat16 partition as a different drive, ubuntu does.

---

### Post by Neural oD on 2009-02-02
k - have u tried manually mounting it. Say you want to mount the linux partition, u'd use something like this: sudo mount /dev/sdb1 /media/test.
BTW /media/test is a directory that i set up with relevant permissions.

---

### Post by Neural oD on 2009-02-02
quick note - the . at the end of the first line should be left off!

---

### Post by dragos240 on 2009-02-02
> **Neural oD said:**
> k - have u tried manually mounting it. Say you want to mount the linux partition, u'd use something like this: sudo mount /dev/sdb1 /media/test.
BTW /media/test is a directory that i set up with relevant permissions.

Oh, it's already mounted, also the fat one is too. It is mounted, but i just can't find the files.

---

### Post by Neural oD on 2009-02-02
ok - run this command: ls -al /wherever_the_mount_point_is

---

### Post by Neural oD on 2009-02-02
if there are no files in there - then it is empty! Try copying files in there and see if they show up with that command

---

### Post by dragos240 on 2009-02-02
```

~$ ls -al /media/disk-1
ls: cannot access /media/disk-1/My renaissance Vocab Finished.odt: Stale NFS file handle
ls: cannot access /media/disk-1/My Renaissncce Vocab.odt: Stale NFS file handle
total 12
drwxrwxrwx 3 harley harley 4096 2009-02-01 11:32 .
drwxr-xr-x 6 root   root   4096 2009-02-02 04:21 ..
-????????? ? ?      ?         ?                ? My renaissance Vocab Finished.odt
-????????? ? ?      ?         ?                ? My Renaissncce Vocab.odt
drwx------ 4 root   root   4096 2009-02-01 11:32 .Trash-0

```

I knew they were in there, but how do i access them.

---

### Post by Neural oD on 2009-02-02
it looks to me as if that partition is a bit corrupt. If you have the files elsewhere - try reformatting that flash. btw - were there meant to be only two files on that partition - the "My renaissance Vocab Finished.odt" and the other?

---

### Post by dragos240 on 2009-02-02
would testdisk fix it?

---

### Post by Neural oD on 2009-02-02
yes - you could use testdisk to fix it - it's in the repositories

---

### Post by dragos240 on 2009-02-02
> **Neural oD said:**
> yes - you could use testdisk to fix it - it's in the repositories

Although testdisk is used for fixing bootable media's could it fix it, it fixed my vista patition, hmm, how would i do this?

---

### Post by Neural oD on 2009-02-02
yes - it's used to fix a corrupt partition table. Have never tried it on a flash myself - but you could give it a go. What i'd suggest - if u have valuable info on it - is to use dd or ddrescue to clone that drive somewhere else. That way if testdisk does something weird - u still have a backup copy of the drive!

---

### Post by dragos240 on 2009-02-02
> **Neural oD said:**
> yes - it's used to fix a corrupt partition table. Have never tried it on a flash myself - but you could give it a go. What i'd suggest - if u have valuable info on it - is to use dd or ddrescue to clone that drive somewhere else. That way if testdisk does something weird - u still have a backup copy of the drive!

But how? I don't really know how to fix it that well

---

### Post by Neural oD on 2009-02-02
I would suggest going to the testdisk site [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) 
They have docs etc there for recovering data - also check out photorec - by the same crowd - also recovery software! 
Hope this helps :)

---

### Post by dragos240 on 2009-02-02
> **Neural oD said:**
> I would suggest going to the testdisk site [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) 
They have docs etc there for recovering data - also check out photorec - by the same crowd - also recovery software! 
Hope this helps :)

nope nothing

---

