---
title: "what is a good Partition lay out on 160gb hard drive"
date: 2009-05-06
forum: General Help
---

### Post by blake7 on 2009-05-06
hi what is a good lay out with one of the Partition with window on it.
im about to load 9.04 on to a new 160gb hard drive so i just like to know what space to give to each area. ie how much for the home folder eta

thank you

---

### Post by x33a on 2009-05-06
that depends on your choice.

i don't like separate home, so would go for

1. 15 GB root (ext4)
2. appropriate swap
3. 15 GB ntfs (for windows)
4. divide the rest into 2 data partitions (ext3)

but if you want separate home, then maybe

1. 15 GB root (ext4)
2. appropriate swap
3. 15 GB ntfs (for windows)
4. rest /home (ext3)

and remember, install windows first, if you don't want the headache of re-configuring grub.

---

### Post by scheuri on 2009-05-06
I do not know why x33a does not like a separat /home, but I STRONGLY suggest that you make one. It is much easier to upgrade and get to your data if something fails (however, make backups all the time!).

I would suggest:
1 to 2 GB of swap
20 GB of /root (but that depends on what you want to install in the end) 
Rest is /home

I would also suggest you use ext3.

If you are using your PC for server purposes (and I am not talking about testing, but real server purposes) the layout and filesystem may vary.

---

### Post by kernow on 2009-05-06
am I missing something would you not want a boot partition, and also as he said to run windows would you not want 
50mb /boot
15gb fat32 first position for windows
15gb ext 3 or ext 4 for /root
swap roughly twice ram
rest fat /home readable by both os

personally I would just use virtualbox to run the needed windows software then be able to use ext3 for partitions

---

### Post by blake7 on 2009-05-08
ok im not going to put windows on how do i start to partions is thier a step by step guid to this..
thank you

---

### Post by blake7 on 2009-05-08
i havew the disk in and i have prepare partition sceen up what do i do next    thank you 

p

---

