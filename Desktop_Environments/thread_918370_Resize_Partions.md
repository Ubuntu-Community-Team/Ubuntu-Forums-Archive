---
title: "Resize Partions"
date: 2008-09-12
forum: Desktop Environments
---

### Post by cantdrive55 on 2008-09-12
So I have a 160GB drive dual booting with XP and Ubuntu. I made the XP partition 110GB and the Ubuntu around 45GB. I realized that I would rather use Ubuntu as the OS but keep all the files on the XP partition so I can still access them in both OS's. 

I have run into an issue though, I want to resize the Ubuntu side down to 15GB and add the remaining 30GB to the XP partition. I was able to resize the Ubuntu down to 15GB but I still have the extra 30 in unallocated and cant get it to merge into XP's side. 

Little help?

---

### Post by kjohansen on 2008-09-13
you will need to move the XP partition so that the XP partition is to the left of the 30 you want to merge with.

So:
....[XP][30]...


Then you can grow the XP.  Gparted will only let you grow to the right.

---

### Post by cantdrive55 on 2008-09-13
I think I have it setup right but when I right click on the XP partition and choose resize/move, it won't let me make it any larger. And the move option is greyed out on the unallocated space.  

I attached a screenshot of gparted.

---

### Post by cantdrive55 on 2008-09-14
bump.

---

