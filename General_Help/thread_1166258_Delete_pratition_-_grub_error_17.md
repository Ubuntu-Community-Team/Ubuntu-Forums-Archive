---
title: "Delete pratition - grub error 17"
date: 2009-05-21
forum: General Help
---

### Post by samuelmaskell on 2009-05-21
Hey guys, 
I just tired to delete my ubuntu partition as I was having trouble with it, needed more space to try win7 and am getting a new HDD tomorrow.  Now when I start up I get a grub error 17 and I have no idea what to do.  I've found some threads on fixing the problem but none have helped because I don't even have ubuntu installed anymore..  I don't even know where to start.

Thanks for your help,
Sam

---

### Post by lindsay7 on 2009-05-21
boot up from you windows install disk. Go to the repair option and get to the command prompt. the type bootrec.exe that will give you some switch options. Try typing bootrec /FixMbr or bootrec /FixBoot.  One of these should work.

---

