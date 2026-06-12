---
title: "swapfile on SSD"
date: 2010-07-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bofak on 2010-07-10
I have heard and read that you shouldn't use a swapfile on a solid-state hard drive because the constant writing to one portion of the drive will soon wear it out and make that part unusable.

When I did my installation I created a partition for a swapfile.  Now I'd like to get rid of it but I've no idea how to go back in and do this (I'm sure it's easy but I'm a total newbie.)

I have the very tiny 4GB drive on my Dell 910.  Running Ubuntu 9.04 (because I couldn't get wifi to work on 9.10 or 10.04, but that's another PITA that I'll come back to when I can find time).

I'd appreciate any advice on the use of a swapfile on a 4GB SSD, and how to get rid of it.

---

### Post by Detonate on 2010-07-10
I don't have a SSD Drive, but in my experience, the swap file is very seldom used anyway.  I think the swap file is not being used often enough to be of concern.  The remainder of the drive is being used a lot more than the swap partition. 

You can control the use of your swap by adjusting the swappiness to use the swap less often.  Read this:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by dleik on 2010-07-10
On your dell mini 9 wireless network.  Hook your mini to a hardwire network, go to hardware drivers under system and update the wireless driver.  Once you have done that, the wireless will work flawlessly.

---

### Post by Zip247 on 2010-07-10
The swap file will only be used if you run out of memory.  If you would like to know how much ram is used.

```
free -m
```

below is what my laptop shows 

```
       total       used       free     shared    buffers     cached
Mem:          1128        530        597          0         31        219
-/+ buffers/cache:        279        848
Swap:         1286         77       1209
```

as you can see my laptop does not have a lot of ram(its old and does not support more).  I am still only using 77MB of swap space.

I also have an eeepc with 40g ssd and 2GB of ram. The swap space is usually not used with just my email and browsing that I use it for.

---

