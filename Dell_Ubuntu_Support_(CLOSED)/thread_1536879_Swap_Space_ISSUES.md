---
title: "Swap Space ISSUES"
date: 2010-07-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by The_Icebud on 2010-07-22
Ok. Well, whenever I went to check my Swap Space, it shows: 

```
phillip@Desktop:~$ swapon -s Filename    Type        Size    Used    Priority
``` with no values. Then when I try to add some it says: 

```
phillip@Desktop:~$ dd if=/dev/zero of=/extraswap bs=1M count=750
dd: opening `/extraswap': Permission denied
```Help?

---

### Post by gbrainin on 2010-07-23
OK, I'm not sure why you're trying to enable a swap file using the dd command, but let's start at the beginning.

Is there a swap partition on your hard drive?

---

### Post by The_Icebud on 2010-07-23
Its my understanding that I only have 2 partitions. One for Win XP and one for Ubuntu 10.04.

---

### Post by gbrainin on 2010-07-23
First, you can double-check whether you have a swap partition by running GParted (System->Administration); you may need to install it, first.

Second, if you don't have a swap partition, you can't activate it.  I think there may be a way to set up a swap file, but that's beyond my expertise.  You can repartition your drive to add a swap partition, if you're comfortable with that sort of thing (again, using GParted).

Third, my understanding is that if you aren't filling up your RAM and requiring paging, you don't really need a swap, anyway.  Unless, of course, you want to use the hibernate function, which I believe saves RAM to the swap space.

---

### Post by The_Icebud on 2010-07-23
I just added a new partition by making my XP partition smaller. I just wonder how exactly to make it into swap space.

---

### Post by wojox on 2010-07-23
Read away [SwapFaq]("https://help.ubuntu.com/community/SwapFaq") and don't forget **sudo**

---

### Post by The_Icebud on 2010-07-23
> **wojox said:**
> Read away [SwapFaq]("https://help.ubuntu.com/community/SwapFaq") and don't forget **sudo**
Thanks! I can't believe I didn't find that before! :D I think I added more than enough swap space. Thanks to both of you!

---

### Post by gbrainin on 2010-07-24
You're welcome, and enjoy using Ubuntu!

---

