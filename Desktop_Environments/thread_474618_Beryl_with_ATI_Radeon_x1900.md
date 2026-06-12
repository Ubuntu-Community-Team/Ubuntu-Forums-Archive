---
title: "Beryl with ATI Radeon x1900"
date: 2007-06-15
forum: Desktop Environments
---

### Post by type_raver on 2007-06-15
Hey guys I have had some issues installing beryl with this hardware setup and I was wondering if any of you with more success could please help me out.

Just to add I have set it up with Nvidia many times with no issues so perhaps it is a driver issue?  I used edgy to install the ati drivers as well.

Cheers.

---

### Post by angryfirelord on 2007-06-15
You need the fglrx drivers. 
```
sudo apt-get install xorg-driver-fglrx
```
Then, edit your xorg.conf and change Driver to say "fglrx".

---

