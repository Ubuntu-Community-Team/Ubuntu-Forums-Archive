---
title: "read/write windows drives?"
date: 2006-07-15
forum: Desktop Environments
---

### Post by detzx on 2006-07-15
I have all my movies and mp3s on my windows drives, I think ntfs..last I knew ntfs was not well worked out in linux so would it be better and safer if I used partition magic to change the partitions to fat32?

I want to be able to read and write from these drives from both Windows and Linux. Will I have to do anything special in linux to get it to write to fat32?

---

### Post by VirtuAlex on 2006-07-15
Just mount it as read/write. I think it will be default, but if it is not you'll have to edit /etc/fstab

---

### Post by detzx on 2006-07-15
> **VirtuAlex said:**
> Just mount it as read/write. I think it will be default, but if it is not you'll have to edit /etc/fstab

You mean in fat32 right, it wont let me mount with write when it's ntfs.

---

### Post by orb9220 on 2006-07-15
I change my ntfs to fat32 with partition magic.

Just be sure to defrag a couble of times before converting

---

### Post by VirtuAlex on 2006-07-15
> **detzx said:**
> You mean in fat32 right, it wont let me mount with write when it's ntfs.

Of course fat32.

---

### Post by VirtuAlex on 2006-07-15
> **detzx said:**
> last I knew ntfs was not well worked out in linux so would it be better and safer if I used partition magic to change the partitions to fat32
By the way, make sure you do not change to fat32 that partition where windows installed. Make separate partition for fat32.

---

### Post by DavidFL on 2006-07-15
> **detzx said:**
> I have all my movies and mp3s on my windows drives, I think ntfs..last I knew ntfs was not well worked out in linux so would it be better and safer if I used partition magic to change the partitions to fat32?

I want to be able to read and write from these drives from both Windows and Linux. Will I have to do anything special in linux to get it to write to fat32?


Apparently NTFS read and write support is done and is reliable with minor problems:

[http://sourceforge.net/mailarchive/forum.php?thread_id=23836054&forum_id=2697](http://sourceforge.net/mailarchive/forum.php?thread_id=23836054&forum_id=2697)

But you may wish to hold off until it is tested more and such. 

Fat32 support right now is pretty bullet proof and working great.  NTFS read support is also great.

---

### Post by Anduu on 2006-07-16
> **DavidFL said:**
> Apparently NTFS read and write support is done and is reliable with minor problems:

[http://sourceforge.net/mailarchive/forum.php?thread_id=23836054&forum_id=2697](http://sourceforge.net/mailarchive/forum.php?thread_id=23836054&forum_id=2697)

But you may wish to hold off until it is tested more and such. 

Fat32 support right now is pretty bullet proof and working great.  NTFS read support is also great.

I installed and set this up today....it is dreamy :p

---

