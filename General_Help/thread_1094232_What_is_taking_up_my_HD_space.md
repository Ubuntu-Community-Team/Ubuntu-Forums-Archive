---
title: "What is taking up my HD space?"
date: 2009-03-12
forum: General Help
---

### Post by ed-koala on 2009-03-12
I'm having a tough time on this though I'd have thought it'd be easy ... I have a 500 gig HD.  Right now 60 gig or so is free space.  When I check disk usage analyzer, it doesn't seem to show 440 gig worth of material.  I checked properties on every folder in filesystem, but I can't see what is using so much room.  My home folder only uses 36 gig, supposedly.  How do I find out why my available space is so low?

---

### Post by ponyexpress on 2009-03-12
Is the whole 500GB in one partition?

---

### Post by ed-koala on 2009-03-12
I'm not sure, how do I check?

---

### Post by insane_alien on 2009-03-12
post the output of 'sudo fdisk -l'

---

### Post by cariboo on 2009-03-12
THe quickest way to check disk usage, is to open an Applications-->Accessories-->Terminal and type:

```
df -h
```

You should get an output that looks something like this:

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             5.8G  4.6G  917M  84% /
tmpfs                 994M     0  994M   0% /lib/init/rw
varrun                994M  108K  994M   1% /var/run
varlock               994M     0  994M   0% /var/lock
udev                  994M  104K  994M   1% /dev
tmpfs                 994M   84K  994M   1% /dev/shm
lrm                   994M  2.4M  992M   1% /lib/modules/2.6.28-9-generic/volatile
/dev/sdb4             143G   47G   89G  35% /home
/dev/sda1             151G   88G   56G  62% /home/storage
```

Your partitions are the lines that start with /dev

Jim

---

### Post by ed-koala on 2009-03-12
Ok, got this checked out.  Still not sure why checking filesystem's properties only shows 32gig used when the drive is almost full, but I used gparted and straightened out my partitions and I'm swimming in disk space, about 675 gig free now.  Damn new PC wasn't even using some space!

These forums are great, found everything I needed and learned some new things too! Thanks

---

### Post by Nano_ext3 on 2009-03-12
Easiest thing to do is use gnomes disk space checker. To run this do Alt+F2 and type "baobob"  This is part of the gnome utilities package and will easily scan your file system and tell you which parts are eating up the most space.  BE CAREFUL, do not delete something you do not know what it is or are unsure.  Consult the forums first or google.

If you do not have disk usage analyzer peform this command in terminal:

"sudo apt-get install gnome-utils"

If you prefer terminal to check diskspace usage, use the command "du" or the more simplistic "df" utility.

Example "du -h /" or "du - hS" , see "man du" or "man df" for more information.


Cheers!

-Nano

---

