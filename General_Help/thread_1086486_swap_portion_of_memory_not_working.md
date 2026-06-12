---
title: "swap portion of memory not working?"
date: 2009-03-04
forum: General Help
---

### Post by abhilashm86 on 2009-03-04
how to start swap portion of memory, i don't know it's just stopped,
you can see results below,
due to this or other reason, ubuntu performance and speed is totally reduced, help me to fix this again.

---

### Post by abhilashm86 on 2009-03-04
here it is notice swap is 0.

---

### Post by geirha on 2009-03-04
Is it listed with this command?
```
swapon -s
```

---

### Post by abhilashm86 on 2009-03-04
> **geirha said:**
> Is it listed with this command?
```
swapon -s
```

abhilash@abhi:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/sda9                               partition	843372	0	-1

what does this indicate? yes used is showing 0, is it swap space?
how to activate swap again?

---

### Post by Zack McCool on 2009-03-04
Your swap appears to be working fine.  Your system is just not using any of it, as you have plenty of memory for what you are doing.

In the swap line in htop, the first number is the amount currently in use, then a /, then the amount available.

---

### Post by abhilashm86 on 2009-03-04
> **Zack McCool said:**
> Your swap appears to be working fine.  Your system is just not using any of it, as you have plenty of memory for what you are doing.

In the swap line in htop, the first number is the amount currently in use, then a /, then the amount available.

oh ok fine, i got it now, so my swap is noting to do with ubuntu speed and performance? actually my system has become slow and all applications have slowed in accessing and performing? have you have any idea?

---

### Post by linux_tech on 2009-03-04
swap is more critical for a system with less RAM, for example less than 512.
If you have 1 GB or more then swap becomes less used. To optimize system there are many good references available.  First monitor to identify the bottlenecks then fix them. Start by checking in top or htop to identify what is using the resources, then look for ways to optimize them or if you can live without them either look for a alternative that uses less or just turn them off.

---

