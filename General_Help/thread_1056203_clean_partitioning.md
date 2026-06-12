---
title: "clean partitioning"
date: 2009-01-31
forum: General Help
---

### Post by Shady3D on 2009-01-31
hi all, I was having a booting problems then i decided to make a clean install.

1. i want to make swap then /boot , /home & /  so **what will be logical and what will be primary?**
2. i want to be able to make a clean upgrade for ubuntu every version so i need to have my programs in a safe place with my setting so about my setting I will create /home in its own partition but [B]how about the programs installed 
[/B]

---

### Post by taurus on 2009-01-31
1.  It doesn't really matter.  But if you know for sure you will only use four partitions on a harddrive, then make them all primaries.  Remember, you can only have four primaries and if you want more than four partitions, you have to make one of those primaries into extended partition and under that extended partition, you can create logical partitions.

2.  All your settings and personal files will be in your $HOME (/home/username).  All the programs that you installed with apt-get/aptitude, synaptic, or/and add/remove will be resided in /usr/bin, /bin, /sbin, etc.

---

### Post by Shady3D on 2009-01-31
so i should create /usr/bin, /bin, /sbin in separated partitions and also i have 160GB Harddisk how to make good use of it

---

### Post by taurus on 2009-01-31
If I have to install Ubuntu on a 160GB harddrive, I would create three primary partitions:  / (10GB), swap (2GB), and /home (whatever left).  

Wait, that is what I have on my machine!  ;)

---

### Post by Shady3D on 2009-01-31
and for windows its primary right?

---

### Post by Yellow Pasque on 2009-01-31
> i want to be able to make a clean upgrade for ubuntu every version
Do you mean that you want to do a complete reinstall of the OS every 6 months instead of upgrading it?

---

### Post by Shady3D on 2009-01-31
well if I managed to make the programs and setting untouched then yes its better

---

### Post by taurus on 2009-01-31
Do you want a dualboot?

It depends how much space you want to install windows on.  I would assume something like

/dev/sda1 = windows (20GB)
/dev/sda2 = / (10GB)
/dev/sda3 = swap (2GB)
/dev/sda4 = /home (whatever left)

As you can see, all four are primaries unless you want to make /home as a logical partition (or maybe both swap & /home).  Again, you can adjust the disk space for windows and / if you choose but remember, all your personal files (pictures, music, movies, downloads, etc.) will go into /home/username so you want to make /home as large as possible but still give / (root partition) enough space to install programs on it.

---

