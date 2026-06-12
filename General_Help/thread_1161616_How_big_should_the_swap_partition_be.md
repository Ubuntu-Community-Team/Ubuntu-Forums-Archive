---
title: "How big should the swap partition be?"
date: 2009-05-16
forum: General Help
---

### Post by Pidgin on 2009-05-16
I have no idea how big the swap should be. I have 2 GB RAM, and it seems the swap is never used. Can I delete the swap?
Thank you.

---

### Post by Hobgoblin on 2009-05-16
There is no minimum size for swap and you can do without it entirely, unless you want to use the hibernate feature.

---

### Post by Vunutus on 2009-05-16
The general rule of thumb is that swap size should be twice the size of your RAM, so in your case, 4GB. That isn't a set rule by any means, but it's what I always use on my systems. Some people like to experiment with running with no swap partition, but I personally wouldn't recommend it.

---

### Post by wolfe747 on 2009-05-16
> **Pidgin said:**
> I have no idea how big the swap should be. I have 2 GB RAM, and it seems the swap is never used. Can I delete the swap?
Thank you.
I'm using Ubuntu Netbook Remix on my Acer Aspire One... I have 1 GB of RAM and have a 1 GB Swap which enables the hibernate feature to work perfectly. If you don't have a laptop you probably won't need to use the hibernate feature, and therefore should be fine without any swap partition, UNLESS you are using programs that require a huge amount of RAM or running many programs at once.

---

### Post by MaximumZeros on 2009-05-16
Hm, if you told Ubuntu to automatically partition your drive to use the entire disk, what does it do about the swap partition?
Does it just make one the same size as your ram for you or what?
Just wondering.

---

### Post by dcstar on 2009-05-16
> **Vunutus said:**
> The general rule of thumb is that swap size should be twice the size of your RAM.....


Maybe in the 1990's, but that is just a myth now and has little relevance (and I wish people would cease repeating it).

---

### Post by MaxIBoy on 2009-05-16
How is it no longer relevant? (I'm curious myself, because I have 3 gigs of ram and 6 gigs of swap.)

---

### Post by lisati on 2009-05-16
Another rule-of-thumb I've encountered is "at least as big as your RAM". I'd guess that it depends in part on what you expect of your machine - too small and you can expect horrid performance from your machine when you start doing more than one or two things with it at the same time, too large and you're wasting valuable disk space.

---

### Post by Pidgin on 2009-05-17
> **wolfe747 said:**
> I'm using Ubuntu Netbook Remix on my Acer Aspire One... I have 1 GB of RAM and have a 1 GB Swap which enables the hibernate feature to work perfectly. If you don't have a laptop you probably won't need to use the hibernate feature, and therefore should be fine without any swap partition, UNLESS you are using programs that require a huge amount of RAM or running many programs at once.
Thank you! Well, I'll disable the swap for several days and see what will happen.

---

### Post by Pidgin on 2009-05-17
> **MaximumZeros said:**
> Hm, if you told Ubuntu to automatically partition your drive to use the entire disk, what does it do about the swap partition?
Does it just make one the same size as your ram for you or what?
Just wondering.
About 500 MB.

---

### Post by Legace on 2009-05-17
If you have less than 2GB of RAM, make the swap partition atleast 2GB.
Otherwise, 2GB or less will be fine :)

I've got 4GB RAM and swap usage is currently 0% with multiple applications running..

---

### Post by bacardiandwatermelon on 2009-05-17
I personally wouldn't have more than 1GB for the swap. I've only got 1.5GB Ram in my laptop and just over 1GB for the swap. I've used System monitor to see how much swap is ever used and it has always been at 0 no matter how much stuff i'm running.

---

### Post by khelben1979 on 2009-05-17
I would advice that you never set your swap above the size of your total RAM if you got lots of it. 2 GB of RAM then you don't need more than 2 GB of swap (probably), in my opinion.

Since the swap is way slower than your RAM memory, I think it would be attractive to turn it off if you had 8 GB of RAM.

It's very hard for me to know what is best for you or anyone else, since it depends much on how the system is being used. What I have written above should be sufficient in most cases, though.

---

### Post by Hobgoblin on 2009-05-18
> **MaxIBoy said:**
> How is it no longer relevant? (I'm curious myself, because I have 3 gigs of ram and 6 gigs of swap.)

You only *need* swap if you don't have enough physical RAM.  If you have enough physical RAM to do what you want then there is no need for swap.

I have 2GB of RAM but only 8GB of "hard drive" (SSD) space on my Eeepc, it would be stupid to waste 4GB of my precious storage on swap I will never need to use.

---

