---
title: "Need Help resolving DPKG error"
date: 2006-07-20
forum: Desktop Environments
---

### Post by shivari on 2006-07-20
UBuntu froze so I had to manually switch the power button when i logged back-in and i try to install something using sudo apt-get, this error appears

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

How do i resolve this error?  When i type dpkg --configure -a, it says that super-user previliges is needed.

---

### Post by meng on 2006-07-20
If you wanted to dpkg --configure -a, you should "sudo dpkg --configure -a" and enter your regular user password when asked.

---

