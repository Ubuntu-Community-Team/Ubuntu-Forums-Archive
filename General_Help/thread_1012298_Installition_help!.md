---
title: "Installition help!"
date: 2008-12-15
forum: General Help
---

### Post by SABOT00 on 2008-12-15
I need help, in vista I shrunk the vista partition so I have 40 gigs of free space. In ubuntu 8.10 I selected the use largest continuous free space option but in the after diagram it shows ubuntu will use 100% of the hard drive. Do I have anything to worry about?

---

### Post by logos34 on 2008-12-15
to be safe you had better select 'manual' option...make a /swap partition (= your installed ram) and then the rest of the space for /
 
partition  mountpoint  type
swap       /swap       linux-swap
root       /           ext3

---

### Post by blazemore on 2008-12-15
Yes, use manual mode.

There should be free space.
Click New Partition.
Type: Primary
Use as: Swap
Size: About the same as your system RAM


And again...
Type: Primary
Use as: EXT3
Size: default
Mount point: /

---

