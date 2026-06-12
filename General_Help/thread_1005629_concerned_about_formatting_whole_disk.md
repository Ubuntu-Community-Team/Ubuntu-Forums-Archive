---
title: "concerned about formatting whole disk"
date: 2008-12-08
forum: General Help
---

### Post by sponsoredwalk on 2008-12-08
I am concerned about a straight format of my small 40gb drive (sda1), this is full although i do not need the contents anymore. My sda1 drive was the original drive and contains Ubuntu 6.04. I later bought a big 300gb drive and installed Ubuntu 7.10 on it (sdb1). I had problems as my 6.04 ubuntu still does not recognise the large drive at all so i am worried something stupid would happen if i were to format the sda1 disk from my 7.10 setup. Would it be a free disk usable from 7.10 if i just formatted the disk with GParted?

---

### Post by lovelyvik293 on 2008-12-08
If you are using the grub installed on the ubuntu 7.10(sdb1), then you can format the sda1.

---

### Post by sponsoredwalk on 2009-01-11
Hi i am wondering what program i should use that will format the entire sda1 disk while i am on the ubuntu 7.10 sdb1 disk, so that i can use it to store music etc as if it were just blank and waiting for data :) Also the middle scroll wheel on my mouse doesn't scroll down anymore, any thoughts why, lol though i will just add a seperate question now anyway, thanks a lot :):):)

---

### Post by oldos2er on 2009-01-11
"i am wondering what program i should use that will format the entire sda1 disk while i am on the ubuntu 7.10 sdb1 disk"

 gparted.

---

### Post by sponsoredwalk on 2009-01-11
will Ubuntu 7.10 recognise the change because i installed 6.10 on sda1, then bought a new disk, installed 7.10 on the new disk and 6.10 still doesnt recognise 7.10 at all!!!! &.10 recognises 6.10 but if i format using the live cd's g-parted it might not recognise a change when i log back in to 7.10, i am a novice at this lol

---

### Post by oldos2er on 2009-01-11
Are you saying you're getting an error when you try to mount your second disk from sda1? Are these SATA drives or IDE? 

 You don't need to boot from CD to format sda1; you can do it from Ubuntu 7.10 as long as sda1 is not mounted.

---

### Post by sponsoredwalk on 2009-01-22
Hiya thanks for the advice, it was using umount /media/sda1 that did the trick, but now i have another problem, i have the formatted disk but it will not let me write, delete or paste anything on it. I have used "Partition Editor" and i have tried formatting it to ext2 and ext 3, i have no idea how to check out this kind of problem... i.e. google for it, and sometimes i cannot even access the disk as i am not root. i have no idea:( thanks again for any further help, very much appreciated

---

### Post by sponsoredwalk on 2009-02-04
Ok, so i am wondering if i were to re-install my windows xp as a dual boot on the newly formatted disk, would 

A) The XP installation process wipe my Ubuntu &.10 on the sdb1 disk, as i seen that installing windows can wipe everything on your pc

B) Windows be accessible from my 7.10 installation, as i had this problem before, in the accessing 7.10 on my sdb1 drive while logged in on my old 6.10 ubuntu on my sda1 drive, really appreciate the help:)

---

