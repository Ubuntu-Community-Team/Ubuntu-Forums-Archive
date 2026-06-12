---
title: "Live CD dies on setting up LVM"
date: 2005-07-08
forum: Desktop Environments
---

### Post by LGLisle on 2005-07-08
The title says it all, I've tried 4 times and it just stops when it gets to:

  "Setting up LVM Volume Groups"      I've waited for up to 10 minutes.

I've got a Duron at 1.4 GHz

Drive 1 is partitioned to
C: 12G
E: 74G

swap 
SUSE ~20G

Drive 2 is:
D: 12G
F: 600M

Any ideas?  Other than chucking the whole thing.  :)

---

### Post by mtron on 2005-07-08
Have you already tried various special boot options? (F2 upon boot gives you some hints)

and the Md5 checksum for the CD iso download?

---

### Post by LGLisle on 2005-07-08
[QUOTE=mtron]Have you already tried various special boot options? (F2 upon boot gives you some hints)[/QUOTE]


Saw no reference to these, no idea they existed.   Will do a check, but have no clue what to use,

[QUOTE=mtron]
and the Md5 checksum for the CD iso download?[/QUOTE]

Where do I find the correct checksum?  I downloaded a MD5 checker, but it seems to want me to enter the correct value.

Thanks for the response though.

---

### Post by LGLisle on 2005-07-09
Well, I looked at the boot options, but didn't see anything that obviously applied.

I tried just letting it run over night, and it did come up. when, I don't know. 

However, I did time some of it.

loading 'isofs' took 4 minutes
starting RAID took 4 minutes (I don't have a RAID)
setting up LVM volume groups took 14 minutes
starting Enterprise VMS took over 30 minutes  (went to bed)

After that who knows.

With this kind of cycle time, I won't be doing much "try it and see" testing.

I guess I'll need to find another Distro.   I also tried Ubunto, with similar results.  :(

---

### Post by MaxFun73 on 2005-07-26
[QUOTE=LGLisle]The title says it all, I've tried 4 times and it just stops when it gets to:
  "Setting up LVM Volume Groups"      I've waited for up to 10 minutes.
[/QUOTE]

I've got the same problem but I'm using an installed version of Ubuntu not the LiveCD  ](*,)

---

### Post by bob27 on 2005-12-22
I also have the same problem.  Mine was caused by Windows ;)

I was installing Nero 7 on my Windows drive and now I can't boot into either Ubuntu or Windows.

---

