---
title: "Problem With wine"
date: 2006-09-04
forum: Desktop Environments
---

### Post by Warcrafter on 2006-09-04
im trying to install the package "wine" and everytime i type sudo apt-get install wine in the terminal this comes up

drumdude234@ubuntu:~$ sudo apt-get install wine
sudo: timestamp too far in the future: Sep  3 21:40:57 2006
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
drumdude234@ubuntu:~$

what do I do?

---

### Post by meng on 2006-09-04
Do you have extra repositories enabled? Wine is in universe, although there is a newer version available in the budget-dedicated[etcetc] repository.

---

### Post by Warcrafter on 2006-09-04
I have no clue what that is... the repositories.

---

### Post by meng on 2006-09-04
Okay, no problem look here and here:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
Repositories are the place to get free software that is set up to run on your Ubuntu system.

---

