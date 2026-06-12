---
title: "memory question"
date: 2006-08-15
forum: Desktop Environments
---

### Post by nbpetts on 2006-08-15
I installed Ubuntu on my computer with 1 gig of system memory spread across two sticks of 512mb ram.  One of the sticks has since burned out, and i don't have the money to replace it at the moment.  Does Ubuntu need to be told that it has less memory to do things with or will that be delt with by the bios?  any thoughts?

---

### Post by 23meg on 2006-08-15
In any case you should remove the burnt memory unit in the first place; did you? If you did, all should be set.

---

### Post by nbpetts on 2006-08-15
yeah i tossed the bad memory stick

---

### Post by 23meg on 2006-08-15
If everything is working as supposed, you should be fine. 

To check how much RAM is detected by Ubuntu, type```
cat /proc/meminfo | grep MemTotal
```

---

### Post by nbpetts on 2006-08-15
thanks thats helpfull.

---

### Post by mchatel on 2006-08-15
> **nbpetts said:**
> I installed Ubuntu on my computer with 1 gig of system memory spread across two sticks of 512mb ram.  One of the sticks has since burned out, and i don't have the money to replace it at the moment.  Does Ubuntu need to be told that it has less memory to do things with or will that be delt with by the bios?  any thoughts?

I'm not sure if you had setup any swap partition space before, but most likely, you will want to adjust that, if it's not too much trouble, since you've just halfed the RAM in your computer.  That's the only thing I can think of that you need to adjust.

---

### Post by nbpetts on 2006-08-15
how would i do that and what settings do you recomend?

---

### Post by 23meg on 2006-08-15
You should be able to resize your swap partition with parted or gparted, which is a graphical frontend to it. Ideal swap size is a big myth and many people have many different recommendations. I tend to side with Con Kolivas' explanation ([http://members.optusnet.com.au/ckolivas/kernel/):](http://members.optusnet.com.au/ckolivas/kernel/):)

> **How much swapspace should I allocate?**

Unfortunately there is not much good documentation on swapspace that is meaningful on today's hardware. As the discrepancy between ram speed and hard drive speed becomes greater each year, the old rule of 2*ramsize is just plain wrong. This was in the old days because the addr space was directly mapped into the first half of the double RAM sized swap, giving an easy translation formula; only the space >> RAM size was usuable as additional space.

Since most of your ram will be filled with cache, you don't need a huge swapspace, just enough to cope with transient periods of pressure.

The size should actually depend on the speed of your hard drive. On current drives I recommend about 256MB of swapspace (no matter how much ram you have). You could double it for a striped raid0 array of swapspace. 

---

