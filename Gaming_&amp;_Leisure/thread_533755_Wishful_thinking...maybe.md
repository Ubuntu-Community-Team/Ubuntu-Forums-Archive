---
title: "Wishful thinking...maybe"
date: 2007-08-24
forum: Gaming &amp; Leisure
---

### Post by Cygnusx-1 on 2007-08-24
I'm wondering if it's possible to set up a way to share game data between my Ubuntu and WinXP partitions.
Say I pick up Bioshock to Supreme Commander today and don't want to wait for someone to figure out how to run it under Cedega/Wine, so I install it under XP. Later on I get it installed under Wine, but I want to access my savedgames and user accounts that are under XP.
Is there any way this can be done? 

Thanks!

---

### Post by wolfger on 2007-08-24
If there is a specific directory for saved games, I think this would be pretty easy. Simply remove the Cedega save dir and set up a symbolic link to the Windows save dir.
Something like:
```
cd <cedega game directory>
rm -Rf saved
ln -s <path to Windows game directory>/saved saved
```
Then anytime Cedega loads from or saves to "saved", it will actually be loading from or saving to <windows>/saved. From the Windows side, nothing appears to have changed.

---

### Post by hikaricore on 2007-08-24
This assumes you have disk write enabled on NTFS or are using a FAT based filesystem for your ***dows partition.

Otherwise this will fail.

---

### Post by wolfger on 2007-08-24
True. I just assumed that on a dual boot system, the appropriate filesystem drivers would be enabled. So I assume that Ubuntu doesn't have NTFS-3G by default, then? Is there an easy way to enable it?

---

### Post by hikaricore on 2007-08-24
> **wolfger said:**
> True. I just assumed that on a dual boot system, the appropriate filesystem drivers would be enabled. So I assume that Ubuntu doesn't have NTFS-3G by default, then? Is there an easy way to enable it?

Not enabled by default, but enabling it is very simple:

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by Cygnusx-1 on 2007-08-24
Wow, thanks, guys. I'll try this this weekend. If it works it'll be the last thing keeping me for using Ubuntu as my primary system.

I'll let you know how it goes!

---

### Post by wishyjr on 2007-08-24
this works for me... sometimes. I wanted the solution you speak of and got a fair way there. some stuff works ok but others just won't work until you install them on the cedega or wine drive. the only way to see is to try. good luck.

---

