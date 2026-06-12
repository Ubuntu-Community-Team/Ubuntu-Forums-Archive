---
title: "Install Question - Partitioning Error"
date: 2007-08-14
forum: Dell  Ubuntu Support
---

### Post by gambler on 2007-08-14
I have a new Dell Inspiron 1521 which I made a mess of when I tried to Install Ubuntu (basically I overwrote Vista - mind, you not necessarily a bad thing, but I was trying to make a Dual Boot machine).

Vista has been reinstalled and works.

Back to Ubuntu...

I've created the correct partitions (swap and /) and started the install.  Then I get an error box with:

"Go back to menu and correct error:
The test of the file system with type FAT16 in partition #1 of SCSI1 (0, 0, 0) (sda) found uncorrected errors"

Looking around here seems to indicate that this FAT16 partition #1 is a Dell specific area of the hard drive.  My question is, can I ignore this message and proceed?  Sounds like people have managed to get it to work, but they don't say if they did something to this FAT16 section first...

Robert

---

### Post by notwen on 2007-08-14
More than likely you have additional partitions created by Dell.  These are likely your restoration partition/partitions.  It shouldn't be too difficult to install Ubuntu alongside Vista.  Pop in your Ubuntu LiveCD and do type the code below in a terminal to show us your current HDD partitions, paste the output of this command here.
```
fdisk -l
```

---

### Post by guguma on 2007-08-14
You can totally destroy those unnecessary partitions by dell. I had them too, wiped them off. And I am having not a single trouble. They use a considerable amount of space and primary partition are if you ask me.

---

