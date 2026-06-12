---
title: "Raid 0 or Raid 1 (10k rpm)"
date: 2010-08-25
forum: Desktop Environments
---

### Post by 1Michael1 on 2010-08-25
So I'm getting a new pc from my aunts husband and it has 2x 35GB disks with 10.000 rpm and another 250 gb (7.200 rpm).
I was thinking of putting it into a raid and run the 10.000rpm disks as the system, but I'm not too certain which one to pick. If I should take Raid 0 and have a 70 gb system drive or go for the security of a Raid 1, unless one of the two disks breaks. But that would only leave me with a 35 gb drive which seems a bit too low.

So what do you guys think?
Should I run it as a 35 GB drive (Raid 1) and store all my software on the second disk instead (250 gb 7.200) and just use the system disk for..oh well, system. Instead of having my programs on the system drive as I've always had before.

Thanks.

---

### Post by dtoronto on 2010-08-25
Raid 1, but I'm always for fail-safe redundancies.

---

### Post by 1Michael1 on 2010-08-26
Bump

---

### Post by paulisdead on 2010-08-26
I vote RAID1 as well.  I run my OS off a 40GB SSD, and it's more than enough space for Ubuntu.  Just use the 250GB for /home.  Just clean up /var/cache/apt/archives/ from time to time, and you should be alright.  35GBs will be plenty for the OS and all your programs.  I have quite a few installed and use less than 10GBs.

If you do pick RAID0, be sure to do regular backups.  With RAID0, you double your chances for data loss, since a single disk failure will lose everything on the array.

---

