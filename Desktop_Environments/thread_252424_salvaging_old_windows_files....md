---
title: "salvaging old windows files..."
date: 2006-09-06
forum: Desktop Environments
---

### Post by kerme8503 on 2006-09-06
I have a lot of songs/just crap on a seperate partitino on my hdd (its in  FAT 32 file system) and was wondering if there is any way i can convert them to a linux ext 3 file system or something so i could have my songs and stuff.  thanks.

---

### Post by Atomic Dog on 2006-09-06
Maybe this will help you:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Once mounted you can move the files or edit fstab and have that partition mounted automatically on boot(you can use the files on the fat fartition instead of moving them).

---

### Post by kerme8503 on 2006-09-06
thank you very much   :D

---

### Post by kerme8503 on 2006-09-06
haha, so i start following the steps, and whe it gets to where you figgure out which partition is the windows one, terminal says my partition from windows is a linix file system.  to top it all off when you edit this one thing and put in :
sudo nano /etc/fstab

the partition the is suposed to be my windows one, dosent even show up.  hmm.  help please :)

---

### Post by kerme8503 on 2006-09-06
BUMP - help please :)

---

### Post by enopepsoo on 2006-09-06
Don't worry about the fstab crap, just go Admin -> Disks.  You will be able to see the partition in there.

You can set up the mount point and everything.

---

### Post by Atomic Dog on 2006-09-13
> **enopepsoo said:**
> Don't worry about the fstab crap, just go Admin -> Disks.  You will be able to see the partition in there.

You can set up the mount point and everything.

That's no fun!  It makes it too easy :D  I just never thought about using the GUI app to do it.  Good call.

---

