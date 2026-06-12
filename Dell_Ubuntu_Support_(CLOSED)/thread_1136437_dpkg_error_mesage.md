---
title: "dpkg error mesage"
date: 2009-04-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chibbyrivera on 2009-04-25
Need help! I was installing updates and shut off computer, now i have an error message as follows:
 
E: dpkg was interruped, you must manually run 'dpkg --configure -a' to correct problem.
E:_cache->open()failed, please report.

---

### Post by lisati on 2009-04-25
From the command line (it's on the Applications->accessories->Terminal menu) type: ```
sudo dpkg --configure -a
```
It will ask for your password - use the same password you used to login. Don't worry if it doesn't show, this is normal

---

### Post by chibbyrivera on 2009-04-25
> **lisati said:**
> from the command line (it's on the applications->accessories->terminal menu) type: ```
sudo dpkg --configure -a
```
it will ask for your password - use the same password you used to login. Don't worry if it doesn't show, this is normal
 
 
 
thank you so much! It worked! I am new to ubuntu.

---

### Post by lisati on 2009-04-25
> **chibbyrivera said:**
> thank you so much! It worked! I am new to ubuntu.

Welcome to Ubuntu. I'm glad I was able to help.
Feel free to ask questions: one day (it will come sooner than you think) you'll find yourself able to answer other people's questions.

---

