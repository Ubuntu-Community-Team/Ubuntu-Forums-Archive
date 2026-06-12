---
title: "strange swap"
date: 2010-06-23
forum: Desktop Environments
---

### Post by birkopf on 2010-06-23
This post doesn't fit anywhere so it goes here ;-)

I have ubuntu 9.10 64bit. No problems since long time until few days ago when I noticed noise from ventilation straight after turning laptop on. No programs were running. Fired up conky to check and 
Both my processors (dual core amd) 100% usage (!)
Temperature 84 Celsius and rising
RAM 56% usage
SWAP - 0% (!)

Now that quite tricky. I rebooted. Problem with overheating disappeard but  swap still is not used. Processor, RAM and rest indicators returned to norm.

- What could cause that strange behavior in your opinions ?

---

### Post by sanderd17 on 2010-06-23
Swap is only used if you RAM gets full or if you hybernate or suspend (one of those, I always swap the words, the one that doesn't use RAM) 
And for your processor, can you look what process is using all power?

---

### Post by wilee-nilee on 2010-06-23
Most people set up to have swap used as little as possible it will slow the processing down in general. Ram=memory is much faster.

---

### Post by birkopf on 2010-06-23
I agree with both of you but (at least my) SWAP never uses 0%. Always something is taken even just 1%. I have checked partition and it seems fine...

---

### Post by wilee-nilee on 2010-06-23
> **birkopf said:**
> I agree with both of you but (at least my) SWAP never uses 0%. Always something is taken even just 1%. I have checked partition and it seems fine...

I don't understand what your saying.

---

### Post by birkopf on 2010-06-24
> **wilee-nilee said:**
> I don't understand what your saying.

I have scanned SWAP partition to see if there is no errors. 

On processes list every one of them uses 0% of processor....

---

### Post by sanderd17 on 2010-06-24
There is no relation between swap and processor use.

On my computer (3 GB RAM) swap almost always uses 0%. Yesterday it was 0.6% because my computer was up for more than 6 days and the ram must have been full one of these days. 

What do you mean by "them" in "On processes list every one of them uses 0% of processor.... "?

---

