---
title: "Bad performance on new PC"
date: 2007-02-13
forum: Desktop Environments
---

### Post by gp2x on 2007-02-13
Hi all

I have a new work PC - its a HP Compaq v-pro.

Intel Duo 1.86Ghz, 2G DDR, 80G sata, Intel 965Q video

The performance sucks. My laptop has similar spec, except it has an ATI video chipset, and it craps on the desktop from a very large height.

For example, I opened the package manager on the desktop to search for something and while I was waiting for it to initialise I had opened it on my laptop, completed the search, and closed it again.

I cant tell where the bottleneck is - hdparm reports decent speeds (similar to my laptop) on the HD. It reports 2G memory ok. 

How can I tell where the problem is? The desktop should be working better than this.

Thanks

---

### Post by dcstar on 2007-02-13
> **gp2x said:**
> Hi all

I have a new work PC - its a HP Compaq v-pro.

Intel Duo 1.86Ghz, 2G DDR, 80G sata, Intel 965Q video

The performance sucks. My laptop has similar spec, except it has an ATI video chipset, and it craps on the desktop from a very large height.

For example, I opened the package manager on the desktop to search for something and while I was waiting for it to initialise I had opened it on my laptop, completed the search, and closed it again.

I cant tell where the bottleneck is - hdparm reports decent speeds (similar to my laptop) on the HD. It reports 2G memory ok. 

How can I tell where the problem is? The desktop should be working better than this.

Thanks

Do a forum search for "disable ipv6".

---

### Post by gp2x on 2007-02-13
wow, thanks a heap - that really seems to have improved things!

Whats up with ipv6 then?

---

### Post by dcstar on 2007-02-14
> **gp2x said:**
> wow, thanks a heap - that really seems to have improved things!

Whats up with ipv6 then?

It basically is the Ubuntu system trying to communicate in a way incompatible with some network environments.

It should realise that IPv6 isn't in use and stop then trying to use it, but it doesn't and has to keep waiting for time-outs before things happen.

It seems to be one of those things that seemed like a good idea in theory, but causes problems for users out in the real world.......      :(

---

### Post by JensenDied on 2007-02-15
darn way of the future and old things that dont support them.

"what we dont communicate over distances with morse code anymore?" sort of thing

---

