---
title: "Gparted magically evaporated my ubuntu"
date: 2010-07-19
forum: Desktop Environments
---

### Post by the_jlx on 2010-07-19
So i rezied my fresh install to get some more space and this is what happens.
any suggestions?
I sure hope so because all my passwords and other stuff was in there.
i guess i be sitting down having beer while refreshing the page lol.
This is gonna be a looong day and night and a very wet one

```
The filesystem size (according to the superblock) is 34007589 blocks The physical size of the device is 17544980 blocks Either the superblock or the partition table is likely to be corrupt! Abort? yes
```

```
sudo e2fsck -b block_number /dev/xxx
``` does not work

---

### Post by philinux on 2010-07-19
> **the_jlx said:**
> So i rezied my fresh install to get some more space and this is what happens.
any suggestions?
I sure hope so because all my passwords and other stuff was in there.
i guess i be sitting down having beer while refreshing the page lol.


```
The filesystem size (according to the superblock) is 34007589 blocks The physical size of the device is 17544980 blocks Either the superblock or the partition table is likely to be corrupt! Abort? yes
```

```
sudo e2fsck -b block_number /dev/xxx
``` does not work

Assuming you're running this from the livecd.

```
fsck -v /dev/sda
```

Replace sda with the correct partition.

---

### Post by the_jlx on 2010-07-19
Next suggestion  :p
Maybe someone finds a challenge here

```
ubuntu@ubuntu:~$ sudo fsck -v /dev/sda6
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
The filesystem size (according to the superblock) is 34007589 blocks
The physical size of the device is 17544980 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>?
```

---

### Post by the_jlx on 2010-07-19
Ok i have a idea but i think it might make me loose stuff from ages back lol
Delete partition and use a file carver to restore the files.
But will this work in this kind of error?
I know from my job i can get files from years back on ntfs but i have only done ext4 2 times and that was just a format.
not some odd partition&superblock schitzophrenia

---

### Post by the_jlx on 2010-07-19
Bump... ?

---

### Post by ks07 on 2010-07-19
Just found this thread which describes the same problem, it seems someone fixed it by simply using resize2fs: [http://www.linuxquestions.org/questions/linux-hardware-18/size-in-superblock-is-different-from-the-physical-size-of-the-partition-298175/](http://www.linuxquestions.org/questions/linux-hardware-18/size-in-superblock-is-different-from-the-physical-size-of-the-partition-298175/)

Don't ask me the proper way to use it though, I haven't a clue! :p

---

### Post by jpl888 on 2010-07-19
```
resize2fs -fp /dev/sda
```

Will force resize2fs to ignore if the volume needs a fsck and print a progress bar.

I have fecked things up with parted before and I wasn't able to recover from the situation. I hope you have better luck.

---

