---
title: "Formatting re-writable media"
date: 2006-02-05
forum: Desktop Environments
---

### Post by aseem_mal on 2006-02-05
Hi. I want to format a DVD RW disk that I have. I have no clues how to do this.:confused: 
 Any ideas please.

Thanks,
A

---

### Post by soulestream on 2006-02-05
make sure dvdrw-tools are installed

"sudo dvd+rw-format -force /dev/hdd" <- where hdd is your device. hdb, hdc, etc

soule

---

### Post by aseem_mal on 2006-02-07
[QUOTE=soulestream]make sure dvdrw-tools are installed

"sudo dvd+rw-format -force /dev/hdd" <- where hdd is your device. hdb, hdc, etc

soule[/QUOTE]

Hi. I tried running that command and it is giving me an error like this:

> 
aseem@goobuntu:~$ sudo dvd+rw-format -force /media/cdrom0
* DVD\uffffRW/-RAM format utility by <appro@fy.chalmers.se>, version 4.10.
:- (unable to open("/media/cdrom0"): Block device required


---

