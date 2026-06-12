---
title: "running quake 3 in ubuntu edgy"
date: 2006-11-30
forum: Gaming &amp; Leisure
---

### Post by rkakkar on 2006-11-30
hello.. i have the full windows version of quake 3 on cd with me. how can i run the same in ubuntu?

---

### Post by pay on 2006-11-30
Look here [http://www.neowin.net/forum/lofiversion/index.php/t252074.html](http://www.neowin.net/forum/lofiversion/index.php/t252074.html) Most of those commands need to be run as root so```
wget ftp://ftp.idsoftware.com/idstuff/quake3/linux/linuxq3apoint-1.32b-3.x86.run
sudo chmod +x linuxq3apoint-1.32b-3.x86.run
sudo ./linuxq3apoint-1.32b-3.x86.run
sudo cp /media/cdrom0/Quake3/baseq3/* /usr/local/games/quake3/baseq3
quake3
```

---

