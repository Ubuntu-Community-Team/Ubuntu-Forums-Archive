---
title: "[SOLVED] swap resize destroyed swap???"
date: 2008-12-28
forum: General Help
---

### Post by djbushido on 2008-12-28
Okay, a clarifier:
I repartitioned my drive, first off.
The way my Xubuntu is set up, it is in an extended partition inside of /dev/sda2. Meaning, all the data (including swap area) is inside of that one partition.
I was going to increase my swap size, so i moved a bit off the end of another partition. I then increased the size of the extended partition, then the swap inside of that. Now when I go to the system moniter, it says that I have 0b swap. What the heck?
Do i just need to run fsck, and if so, how?
Or am I just going crazy???(don't answer that...)

---

### Post by dcstar on 2008-12-28
> **djbushido said:**
> Okay, a clarifier:
I repartitioned my drive, first off.
The way my Xubuntu is set up, it is in an extended partition inside of /dev/sda2. Meaning, all the data (including swap area) is inside of that one partition.
I was going to increase my swap size, so i moved a bit off the end of another partition. I then increased the size of the extended partition, then the swap inside of that. Now when I go to the system moniter, it says that I have 0b swap. What the heck?
Do i just need to run fsck, and if so, how?
Or am I just going crazy???(don't answer that...)

You changed the UUID of your swap partition, alter your /etc/fstab file to reflect the change.

---

### Post by bodhi.zazen on 2008-12-28
See this thread if you need assistance :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by djbushido on 2008-12-28
okay, made an fstab backup, used the tutorial, and changed the UUID.
Will restart and find out, will post back later.
Also - bodhi - is your avatar the FC10 preview artwork "invinxible"?

---

### Post by bodhi.zazen on 2008-12-28
> **djbushido said:**
> Also - bodhi - is your avatar the FC10 preview artwork "invinxible"?

LOL, good call ;)

---

### Post by djbushido on 2008-12-29
Okay, now when I go to system moniter, the swap is showing up fine. thank you guys for your help! (btw, why do you have fedora in ubuntu?)

---

### Post by bodhi.zazen on 2008-12-30
I liked the picture, I run multiple OS, but I am not trying to make a statement.

Fedora 10 had, IMO, simply stunning artwork.

---

### Post by djbushido on 2008-12-31
Just kidding, i recently installed FC10 overtop Xubuntu. Anyway, thank you guys once again for your help, I really appreciate it.

---

