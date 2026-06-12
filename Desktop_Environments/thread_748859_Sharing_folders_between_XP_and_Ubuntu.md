---
title: "Sharing folders between XP and Ubuntu"
date: 2008-04-07
forum: Desktop Environments
---

### Post by nu2ubuntoo on 2008-04-07
Hi, 

I am running a Dual boot system with XP Pro and Fiesty. 

I want to be able to access certain folders from both platforms, is this possible and if so how? 


Thanks in advance

---

### Post by prshah on 2008-04-07
> **nu2ubuntoo said:**
> 
I want to be able to access certain folders from both platforms, is this possible and if so how? 


In linux, install ntfs-3g ```
sudo apt-get install ntfs-3g
```. No need to do this in 7.10, it's done by default, but you need it in 7.04.

In Windows, you can install the ext2/3 IFS drivers. [www.fs-driver.org](www.fs-driver.org) to access your linux partition. Word of caution though; DONT access since you can seriously damage your linux filesystem UNLESS you are in ReadOnly mode. (You will get the option during IFS driver installation).

---

### Post by nu2ubuntoo on 2008-04-07
Thanks heaps for the quick reply....

I will give it a go and let you know how it went. 

Thanks again..

---

