---
title: "Partition qustions"
date: 2009-06-09
forum: General Help
---

### Post by rrvega on 2009-06-09
Hey, i've just installed ubuntu 9.04, have windows xp as well. I have a 320gb hard drive, have set xp and ubuntu to 25gb partitions each, now I want to know how to create a partition inside ubuntu that can be accessed by both ubuntu and xp. Is it posible to create one were you can both read and right?

Currently useing ext3 with ubuntu and ntfs on xp, tried creating a fat32 partition but windows wanted to format into ntfs before it would left me view it.

---

### Post by merlinus on 2009-06-09
The partition could not go inside ubuntu, because that is ext3 and not accessible by windows.

You can format the shared partition as ntfs, as ubuntu will easily read and write to it.

---

### Post by synapsys on 2009-06-09
Your best bet is ntfs. It has the best support in both operating systems. Create a new partition (e.g. not inside ubuntu) and format it to ntfs. XP will have no problem with it and make sure ntfs-3g is installed on your Ubuntu installation and you should be fine.

---

### Post by rrvega on 2009-06-09
Thanks :)

Were abouts would I get ntfs-3g?

---

### Post by xngk on 2009-06-09
Go to applications>add/remove search for NTFS Configuration Tool, install it, and then run it in System>admin. Thats what worked for me and my second HDD at least.

---

