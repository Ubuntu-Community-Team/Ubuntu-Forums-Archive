---
title: "NTFS Partition is not visible"
date: 2009-05-19
forum: General Help
---

### Post by emman pacatang on 2009-05-19
I installed ubuntu 9.04 via wubi and perfectly working except that it cannot see the ntfs partition where my xp is installed. Some of my files are installed on that partition, drive c. Is there any way to access my drive c which is ntfs partition? By the my xp is also perfectly working. Thank you.

emman

---

### Post by lukeozade on 2009-05-19
Have you taken a look at [http://www.linux-ntfs.org/doku.php]("http://www.linux-ntfs.org/doku.php") although I'm sure Xubuntu 9.04 has ntfs support anyway..

Somneone asked a similar question here and it was resolved [http://ubuntuforums.org/showthread.php?t=540287]("http://ubuntuforums.org/showthread.php?t=540287") However it is quite old.

---

### Post by Legace on 2009-05-19
Try and have a look in the /media directory.

If you can't find anything, open Applications > Accessories > Terminal and type in:
```
sudo fdisk -l
``` 
and post the output here.

---

