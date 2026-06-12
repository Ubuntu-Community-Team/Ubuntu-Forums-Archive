---
title: "Swap Not in Use? Waste of space"
date: 2009-04-15
forum: General Help
---

### Post by kehon on 2009-04-15
right now i've got 2GB of ram and 3GB swap space everytime now matter how much stuff i'm running eclipse you name it ubuntu 8.10 is only using 5% of the swap space what the hell man what a waste of space how can i tell it to use more swap cause its a big wast of space on a 120GB hard drive dual boot vista 64

---

### Post by B4RR13N705 on 2009-04-15
As i remember, ubuntu only use the swap space when the RAM is empty, so if your machine is not using too much the swap, it means that the RAM is pretty nice, nothing to worry about!

---

### Post by namegame on 2009-04-15
You actually don't want it to use more Swap. Swap is exponentially slower than your RAM.

Swap is basically similar to a paging file found in Windows sytems. When you have to use your Swap, hardrive reads/writes are occurring which are significantly slower than RAM accesses.

I would imagine that you could decrease the size of your swap partition to something much lower and you should be fine. Maybe you could start it at 1 GB and work your way down from there.

---

### Post by Heeter on 2009-04-15
Be glad that your setup isn't using the swap.

As previous mentions, if your machine starts using the swap, then you need to upgrade.


Heeter

---

### Post by paradigm2 on 2009-04-15
> **kehon said:**
> right now i've got 2GB of ram and 3GB swap space everytime now matter how much stuff i'm running eclipse you name it ubuntu 8.10 is only using 5% of the swap space what the hell man what a waste of space how can i tell it to use more swap cause its a big wast of space on a 120GB hard drive dual boot vista 64

Pretty much what everyone else said. 

Also I would just leave it alone.  If it is finally needed and you don't have it because you reduced its size, then you will run into problems.  Consider it insurance.  It isn't really wasted at all.

Now if you had a 10GB swap space it might be a different story...  You might get away with making it 2GB instead of 3GB, but really I'd just leave it alone.

---

### Post by kehon on 2009-04-16
cool thanks wasnt sure what it was for really knew it had something to do with memory

---

### Post by dizzle1234 on 2009-04-16
I may be wrong, but I read some place that Swap is used by certain applications. In particular, when running graphics-processing or music-processing programs (RAM intensive programs). I would imagine that *older[I]* software in particular uses this.

---

### Post by paradigm2 on 2009-04-16
> **dizzle1234 said:**
> I may be wrong, but I read some place that Swap is used by certain applications. In particular, when running graphics-processing or music-processing programs (RAM intensive programs). I would imagine that *older[I]* software in particular uses this.

Well first your physical RAM is used.  Then once that is exhausted or a certain percentage is exhausted, swap is used.  A program might require a lot of memory, such as perhaps a video editing program when working with a huge file.  In that case it might run into your swap very easily.  If it exhausts your swap space, there is I believe a chance a failure.  I see a large swap space as insurance.  My swap is 2.5 GB and 0% is being used right now, though I have seen as much as 7% used in the past and I haven't done anything very memory intensive yet.

---

### Post by PriceChild on 2009-04-16
As I understand it, if you run out of memory, the kernel picks processes out of a hat almost nondiscriminently to determine which one to kill. You don't want this.

---

### Post by Windsurfer619 on 2009-04-16
> **PriceChild said:**
> As I understand it, if you run out of memory, the kernel picks processes out of a hat almost nondiscriminently to determine which one to kill. You don't want this.
It picks the one that wants more memory when there isn't any, and if the process doesn't do proper error checking, it will likely segfault and commit suicide;)

---

