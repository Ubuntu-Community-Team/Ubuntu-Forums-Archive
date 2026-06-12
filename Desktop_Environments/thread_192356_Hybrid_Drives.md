---
title: "Hybrid Drives"
date: 2006-06-08
forum: Desktop Environments
---

### Post by tebibyte on 2006-06-08
Does Dapper currently support Hybrid Drives (or Hard drives that use flash memory as a cache)?

If not, It might be wise to support the feature in Edgy, in order to be one equal grounds with Microsoft.:-k :-D 

Thanks,
Max

---

### Post by NESFreak on 2007-07-26
I'd like to reopen this thread. Is there a way to store part of your operating system transparently on flash mem? (like compact flash (realatively cheap, and easy to connect to your pc)) If so, how to do it? Is there already a sort of automated solution for this? Or something which dynamically updates? And if to do it manually which directories should be stored on it (should fasten up the boot process while limiting the data written to it)

Anyway as soon as 7.10 comes out i'll try it out on a 512MB or 1GB CF card.

NESFreak

---

### Post by kerry_s on 2007-07-26
not worth it, your better off with just more ram.

---

### Post by mcduck on 2007-07-26
> **tebibyte said:**
> Does Dapper currently support Hybrid Drives (or Hard drives that use flash memory as a cache)?

If not, It might be wise to support the feature in Edgy, in order to be one equal grounds with Microsoft.:-k :-D 

Thanks,
Max

Cache on hard disks doesn't need any support from your operating system. It's handled by the disk itself. (pretty much very disk sold today already has some cache memory, typically around 8MB. Only new thing in these hybrid drives is that they use more but slower memory as cache).

---

### Post by NESFreak on 2007-07-26
> **mcduck said:**
> Cache on hard disks doesn't need any support from your operating system. It's handled by the disk itself. (pretty much very disk sold today already has some cache memory, typically around 8MB. Only new thing in these hybrid drives is that they use more but slower memory as cache).

it's doing a bit more than that, it stores frequently accessed data, like the parts of the os used when booting. And keeps them there, so the next time used it'll load faster. It's a bit like putting everything except /home and only parts of /usr on a faster medium, with faster reading speed and access times, lowering the loading times.

Problem is, i don't know how much it would help me. I couldn't really find any benchmarks and stuff. But i do have a usb stick containing slax, which is fast when u use the toram cheatcode. Now ofcource flash mem isn't as fast as ram. But even without putting the whole thing in ram, it still loads faster than from a hard disk.  So anyone already running ubuntu from flash?

---

### Post by kerry_s on 2007-07-26
no your just splitting hairs, distro's that use the "toram" take longer to load because it has to be copied over, also that limits there size to be able to fit fully into ram, which in turn limit's the amount of ram, that can actually be worked with. booting a regular distro, you in fact get the same effect, but your ram has not already been filled up, it will only keep in ram the actual applications that you use. only more ram & a faster disk/hd will see improvements in speed. You might see some improvement using a cf card as your hd via adapter, but than you would be limited by the performance of the card. you can gain some performance by using the usb as a swap, but it would only be use full if you have low ram and are regularly dipping into swap. installing any thing on usb to run will be limited by the speed of usb 2.0, so you won't gain any speed there, it will just be slower than a hd, unless you have got the slowest hd in the world. :) the quest for speed is a tricky one, newer is faster.

---

