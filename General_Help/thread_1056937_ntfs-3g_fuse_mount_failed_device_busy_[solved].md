---
title: "ntfs-3g fuse mount failed: device busy [solved]"
date: 2009-02-01
forum: General Help
---

### Post by aroddo on 2009-02-01
My system worked just fine and ntfs volumes were mountable out of the box (using Ubuntu 8.10).
I installed dmraid for my nvidia fakeraid and that worked well, too (even after rebooting without ******* up my system like last time). 

I got overconfident and installed ntfs-config. Afterwards every time I wanted to mount ntfs partitions I got a "*device busy*".

After searching around and not finding a solution my inept mind could comprehend I simply settled for manually editing the fstab and replacing device by mapped entries:

Before
```

...
/dev/sdc5  /media/D: ntfs-3g defaults,locale=de_DE.UTF-8 0 0
``````

...
/dev/mapper/sil_agagddbgfaba5  /media/D: ntfs-3g defaults,locale=de_DE.UTF-8 0 0
```And it works. :popcorn:

I'm not too sure about what the problem is but I think dmraid made the devices busy. Maybe it's even responsible for mapping them (I really don't know). 

Anyway, this solution worked for me without having to understand the problem, hehe.

It might be a bit tricky to identify the mapped volumes you are looking for, but I'm sure there's a way to find out without just trying blindly.

Cheers!

---

