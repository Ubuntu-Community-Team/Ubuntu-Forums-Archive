---
title: "Swap Partition??"
date: 2006-01-09
forum: General Help
---

### Post by jonathanm on 2006-01-09
ive got ubuntu all set up but on the install i made a 5gb partition for the swap.  now as i understand it, this is sort of like RAM.  I know for a complete fact that i dont have this much RAM (mor like 256mb), is there any way of changing a setting so that it uses the swap partition in preference to the RAM that i have?

Thanks

---

### Post by vruum on 2006-01-09
Short answer. Yes, there probably is, but there's no reason you would want to, swap is significantly slower than ram. I might be mistaken, but as far as I understand, swap functions as an addition to ram, meaning, when you're out of ram, the system wil start swapping, and you will feel this as a decrease in performance.

---

### Post by Tuf on 2006-01-09
I dont think so, but if you only have 256mb it will be using it.  The swap is alot slower than your system memory so you wouldn't want it to replace your RAM.

---

### Post by steve.horsley on 2006-01-09
No. It uses swap when it runs out of RAM and needs more. Using swap is **very** slow compared to using RAM because of the need to read and write the disk. 

Most people will tell you that 5GB swap is more than you need (I have 1G) , but now you have done it I see little point in changing it. Just relax and let the operating system use memory as it sees fit.

---

### Post by jonathanm on 2006-01-09
thanks, i didnt realise that it was slower, ill leave it then.  i just wanted to make use of the space i wasted, bigger isnt always better obviously

---

### Post by leech on 2006-01-09
I wouldn't go much beyond 1gb of swap, so if you ever have to re-install for some reason, remember that next time :D

Swap is in essence the same as the pagefile is under Windows, except that swap (much more intelligently) resides on it's own partition, which eliminates the need to defrag it.

Anyone who has ever had their pagefile become fragmented knows how much it will kill your windows performance.

Leech

---

### Post by dcstar on 2006-01-09
[QUOTE=jonathanm]thanks, i didnt realise that it was slower, ill leave it then.  i just wanted to make use of the space i wasted, bigger isnt always better obviously[/QUOTE]
Swap space is just one component of your system's "Virtual memory", the other component is the RAM and they combine to make up the VM you have available.

Your system will attempt to keep as many active processes as it can in RAM, and then move the inactive (or last used) ones into swap (and back again, when they become active).

The amount of processes you can have running is limited by the available VM, so with 5G of swap you could run quite a lot of memory intensive processes........

There used to be "Rules of thumb" like have as least as much swap space allocated as your RAM, but in reality these were from the days when RAM (and disk space) were a lot more expensive than they are now, so there were a lot of compromises in this area - these days it is use as much of both as you can (within reason......), just have enough (overall) VM for efficient operation of you system - with a bit more swap space available for possible future requirements.

In systems with high demands on swap space, this resource is usually located on a separate disk(s) so VM operations do not affect system performance as much as they would by sharing a drive used for other purposes.

So yes, 5G is basically a waste of disk space, but unless you need it for something else, it won't do any harm having it there.

---

### Post by snick on 2007-03-29
Hello.

My swap file is inactive after booting unless turned on manually via gparted.

possibly result of having repartitioned hdd after ubuntu 6.10 install over win 2k.

--had to edit grub + menu.lst  re:  hdd partitiones referenced.


Q:  How can I set swap drive to be active / enabled on boot ?

Thanks.

---

