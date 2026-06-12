---
title: "Use a flash drive as ram??"
date: 2009-02-07
forum: General Help
---

### Post by AirbusFreak on 2009-02-07
Hi there, I heard from another forum that you can use a flash drive as RAM in Ubuntu... it was something called "swap".
I don't know what it is but I would really appreciate any response.

---

### Post by mb_webguy on 2009-02-07
Not really.  But sort of.  Yes.

Swap in the Linux world is essentially the same thing as virtual memory in Windows.  It's a section of the hard drive where the system writes information from memory that isn't being used often (such as open programs that you're not currently using) or when there isn't sufficient room in memory.  You can actually designate any storage as swap, including a flash drive.  However, while flash storage itself *can* be very fast indeed, USB transfer speeds are *not* when compared to internal hard drives.  So it would be better to use a swap file or swap partition on an internal hard drive than to use a USB flash drive.  Plus, flash drives have a limited number of read/writes.  Using a USB flash drive in this manner will rapidly reduce its lifespan.

---

### Post by HavocXphere on 2009-02-07
Probably possible...but won't be very effective and not worth the hassle imo. Especially if you've got a decent amount of RAM anyway.

Compared to RAM, flash drives are Sssslllloooww.

edit: woot 100 posts

---

### Post by mb_webguy on 2009-02-07
> **HavocXphere said:**
> edit: woot 100 posts

Congrats!  :popcorn:

I was pretty proud myself when I hit 1000 a couple of weeks ago.  (Not that I'm trying to belittle your accomplishment or anything.  I just can't believe I've made that many posts...)

---

### Post by AirbusFreak on 2009-02-07
ok, well i think it will be worth it in my case, i am using a toshiba laptop with only 300meg ram. so where do i access "swap" and how do i use it????? i am still confused??

---

### Post by Monotoko on 2009-02-07
Well, if you have installed ubuntu it will have automatically given itself a swap partition on your harddrive and will be using it. Just leave it as it is my friend, dont try and use a flash drive, as is pointless because one on your harddrive will clearly do a better job than one on your USB

---

### Post by TheLions on 2009-02-07
> **AirbusFreak said:**
> ok, well i think it will be worth it in my case, i am using a toshiba laptop with only 300meg ram. so where do i access "swap" and how do i use it????? i am still confused??

to use flash as virtual memory you'll need to format your flash drive as swap using Partition editor (can be installed with: sudo apt-get install gparted):
1)select your drive (example: /dev/sdc)
2)unmount partition
3)format as swap
4)mount

reboot if necessary

---

### Post by dcstar on 2009-02-07
> **Monotoko said:**
> Well, if you have installed ubuntu it will have automatically given itself a swap partition on your harddrive and will be using it. Just leave it as it is my friend, dont try and use a flash drive, as is pointless because one on your harddrive will clearly do a better job than one on your USB

Good advice, and using a flash device in this way will only kill it prematurely as these things only have a finite amount of write cycles.

To sum up, using a flash drive in this way will give you a slower system that will eventually die when the flash drive dies - hardly an option worth pursuing.

---

### Post by AirbusFreak on 2009-02-08
ok so, in vista.. does it ruin you sd card??

---

### Post by mb_webguy on 2009-02-08
It definitely shortens the lifespan, yes.

---

### Post by AirbusFreak on 2009-02-09
OK, Thanks for you help, I installd 512 meg of swap from my hard drive and its great!

---

### Post by Slim Odds on 2009-02-09
> **AirbusFreak said:**
> ok so, in vista.. does it ruin you sd card??

Vista does not use flash as swap. It uses it for static data that is more frequently read and not frequently written.

[http://en.wikipedia.org/wiki/ReadyBoost](http://en.wikipedia.org/wiki/ReadyBoost)

---

