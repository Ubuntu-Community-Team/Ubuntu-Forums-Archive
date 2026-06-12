---
title: "2nd sata drive question - storage/programs"
date: 2006-08-20
forum: Desktop Environments
---

### Post by thoffland on 2006-08-20
When I first installed my system I was trying to install it as a RAID 0 but that didn't work out, so I have this 2nd sata sitting here that I used for temporary storage until I cleaned and formatted my 120g IDE HD. 

Now I'm wondering if I can install programs to the 2nd sata instead of the main drive since they're both 37gigs each and I'm worried about running out of space on the main one. 

Can I just map /usr/bin and /etc folders to the 2nd sata?? If so, what would be the right procedure? 

Thanks!!

---

### Post by VirtuAlex on 2006-08-20
I think it is better to leave /etc alone, but move whole /usr. Approximate steps:
1. make a partition of desired size on sata
2. mount it in /mnt
3. copy everything sudo cp -a /usr /mnt
4. umonut /mnt
5. add new partition mounting to /etc/fstab
6. delete everything from /usr (or better mv it somewhere, just in case)
7. mount -a

---

### Post by thoffland on 2006-08-21
Thanks! I'll back everything up and see if I can get it to work. 

I appreciate the help!!

---

### Post by VirtuAlex on 2006-08-21
good luck

---

