---
title: "low disk space"
date: 2009-12-09
forum: Desktop Environments
---

### Post by itresources on 2009-12-09
hav windows and ubuntu running side by side but i want to increase the space allocated for ubuntu coz wen i try to install ubuntu updates the update manager says
 low disk space. my total hdd space is still plenty

---

### Post by Fafler on 2009-12-09
First, this thread should be moved to the correct subforum.

It is possible to resize the partitions, but i wouldn't recommend it unless you're experienced with these kind of things.

Do you have access to your Windows partition from Ubuntu? Do you have any stuff, like MP3 files, you can move to the Windows partition?

Try opening a terminal and typing df -h and post the output here.

---

### Post by Kevbert on 2009-12-09
Welcome to the forums.
Please run these commands via Applications-Accessories-Terminal
```
sudo apt-get clean
sudo apt-get autoclean
```
How many versions of Ubuntu do you have on your PC ? (example 2.6.28-4, 2.6.28-5 etc which you can see in the grub startup menu).

---

