---
title: "new ubuntu user"
date: 2006-01-10
forum: Desktop Environments
---

### Post by javvad on 2006-01-10
hi fellos
First of all happy new year to every one.
I'm a brand new user of ubuntu. First time i have installed ubuntu on my machine. As by default i am not a root user i cant open my NTFS partitions. I dont have rights to open them. Only root user can access them. 
Who can i use sudo to open the hard drive partitions.
I'll be thankful if somebody help me out.


Javvad Gillani

---

### Post by brohan on 2006-01-10
sudo chmod -R 444 /path/to/ntfs/partiton
That should do it, if you have them mounted.

---

