---
title: "Ubuntu doesn't detect my SATA drive"
date: 2006-07-19
forum: Desktop Environments
---

### Post by z3r0-c0d3r on 2006-07-19
After I installed Ubuntu I added a 120GB SATA hard drive (took it out because my brother was using it to back up some stuff) but Ubuntu doesn't see it! even in disk-admin it doesn't appear but it works on XP and it used work on breezy, bios sees it as well.

Can someone help please?
Thanks

---

### Post by indytim on 2006-07-19
Just a thought, did you install it as a slave or master?

IndyTim

---

### Post by z3r0-c0d3r on 2006-07-19
I'm not sure but i think its slave i'll check and tell you

---

### Post by theCore on 2006-07-19
> **indytim said:**
> Just a thought, did you install it as a slave or master?

Serial ATA doesn't have masters or slaves, just one device per cable.

---

### Post by Ocxic on 2006-07-19
does "sudo fdisk -l" show it???

---

### Post by kinematic on 2006-07-19
just a thought but it has te be mounted in order for ubuntu to see it.
what happens if you do:
sudo mkdir /media/sda#
sudo mount /dev/sda# /media/sda#
if that works add the appropriate entry's in fstab.

---

### Post by z3r0-c0d3r on 2006-07-25
I removed the cable and put it back and it worked for a while, but after a reboot it disappered again, it shows up sometimes and sometimes it doesn't!!

---

