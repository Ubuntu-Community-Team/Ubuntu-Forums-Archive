---
title: "Second internal hard drive"
date: 2009-02-14
forum: General Help
---

### Post by spongemonkey on 2009-02-14
Hi guys,

My "1TB" internal HDD arrived today and its all bolted in place. I intend to use it simply to store files to keep off my main filesystem disk. I partitioned and formatted it as ext3 using gparted, then ran

```
sudo mkdir /media/storage
```

which is where I want to access the disk, then

```
sudo mount -t ext3 /dev/sdb1 /media/storage
```

My disk is now mounted, but I'll want this to mount automatically on boot, so that's my first question.

Seondly, on opening up the properties window for my newly mounted disk I get this:

[ATTACH]103359[/ATTACH]

46.8GB???? What have I done wrong to have that much used already?

(btw I deleted a folder on the newly created disk called lost+found, which was empty anyway)

Thanks

---

### Post by Elfy on 2009-02-14
lost and found will get created again - fsck uses it

the 48Gb is probably the overhead which is kept for disk full scenarios - 5% - you can adjust that figure

```
sudo tune2fs -m 1 /dev/sdb1
```
would change it to 1%

you need to add the drive to fstab [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

```
gsksudo gedit /etc/fstab
```

Along the lines of 

/dev/sdb1 /media/storage ext3 user 0 2

---

### Post by spongemonkey on 2009-02-14
perfect

---

