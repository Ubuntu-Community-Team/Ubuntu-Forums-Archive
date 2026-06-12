---
title: "Mount as read/write ?"
date: 2009-02-14
forum: General Help
---

### Post by stevebush on 2009-02-14
I have 2 partitions:
1. Mac OS Leopard
2. Windows 7 beta

I have messed up Leopard system files and need to access the partition to sort out the system files. I am using the Ubuntu 8 Live disk.

When I click on Leopard partition, its mounted as read-only so I cant edit files. How do I gain complete access of the partition ?

I need to delete and move some files.

Thanks.

---

### Post by louieb on 2009-02-14
I don't do Apple. But it looks like you need to install package **hfsutils** or package **hfsplus** depending on the format of your partition. ( hfs or hfs+). Don't know how you would find out. 

to install open applications>accessories>terminal and run
```
sudo apt-get install hfsplus  
```

[http://ubuntuforums.org/showthread.php?p=5944133](http://ubuntuforums.org/showthread.php?p=5944133)

Might want to report your post and get it moved to the Apple section of the forum. Good Luck.

---

### Post by stevebush on 2009-02-14
> **louieb said:**
> I don't do Apple. But it looks like you need to install package **hfsutils** or package **hfsplus** depending on the format of your partition. ( hfs or hfs+). Don't know how you would find out. 

to install open applications>accessories>terminal and run
```
sudo apt-get install hfsplus  
```

[http://ubuntuforums.org/showthread.php?p=5944133](http://ubuntuforums.org/showthread.php?p=5944133)

Might want to report your post and get it moved to the Apple section of the forum. Good Luck.

It says: Couldn't find package hfsplus
Same for hfsutils

Any other way of mounting it as read/write ?

---

### Post by stevebush on 2009-02-15
Problem solved now. I disabled journaling as Linux cannot write to Journaled partitions!

---

