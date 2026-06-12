---
title: "Please help with Windows partitions."
date: 2009-01-08
forum: General Help
---

### Post by csh on 2009-01-08
I reinstalled Ubuntu 8.04 by clicking "Install inside Windows" in Ubuntu CD autorun menu.

I installed it in my second partition (D: drive).

However, in Ubuntu, when I go to places -> Computer, I only can see a partition which I used to install Windows. I want that my second partition (D: drive) to be appeared in places -> Computer so that I can easily mount it.

How to do it?

---

### Post by namdung on 2009-01-08
Since **D** Drive is where u've installed Ubuntu using WUBI, it will be available in a folder called **host** in Filesystem. 

To make it available in *Places*, just drag the **host** folder to the left panel alongside *Documents, Music etc*.

---

### Post by csh on 2009-01-12
> **namdung said:**
> Since **D** Drive is where u've installed Ubuntu using WUBI, it will be available in a folder called **host** in Filesystem. 

To make it available in *Places*, just drag the **host** folder to the left panel alongside *Documents, Music etc*.

Thanks!

---

