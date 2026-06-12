---
title: "What is the ideal swap file size?"
date: 2009-03-02
forum: General Help
---

### Post by Predtech on 2009-03-02
Hi guys, can someone please tell me is there a general guide to stick to when deciding what size to make a swap partition?
Currently i have a 62GB drive and i use a 10GB swap partition.
Should i be using a smaller swap??

Thanks

---

### Post by Simian Man on 2009-03-02
> **Predtech said:**
> Hi guys, can someone please tell me is there a general guide to stick to when deciding what size to make a swap partition?
Currently i have a 62GB drive and i use a 10GB swap partition.
Should i be using a smaller swap??

Thanks

That is definitely too large - especially for such a small hard drive.  I believe that Linux can't even use that much swap space (I forget the upper limit).  I generally make the swap partition the minimum of 2 times the amount of memory and 2 gigs.

---

### Post by Rallg on 2009-03-02
Those with solid-state drive (SSD) rather than hard drive (such as my Dell mini 9) are told that any swap may reduce the lifetime of the storage, as the solid-state drive tolerates fewer write cycles than does a hard drive. Swap is write-intensive.

So, if your computer uses SSD, consider using no swap, particularly if you upgraded RAM to 2Gb. That's enough for most applications. If you do a lot of multi-tasking or heavy calculation (such as 3D graphics) then you probably should not be using a small SSD machine.

---

### Post by jpeddicord on 2009-03-02
I use no swap file at all with 2 GB of RAM. Swap is nice to have if you have a lot of applications open or for recovering when something goes wrong and all of your memory is used, but it is also very slow when it is being used. So, rather than have my swap partition be used when memory usage get high, everything will still stay in RAM. It means that hibernate doesn't work (you need swap space to hibernate) but I prefer a more responsive system.

---

### Post by Slim Odds on 2009-03-02
> **Rallg said:**
> So, if your computer uses SSD, consider using no swap, particularly if you upgraded RAM to 2Gb. That's enough for most applications. If you do a lot of multi-tasking or heavy calculation (such as 3D graphics) then you probably should not be using a small SSD machine.

Multi-tasking or heavy calculation does make a difference as these happen in RAM. It's only if the application needs to write a lot a data that there would be issues with SSD.

---

### Post by damis648 on 2009-03-02
> **jacobmp92 said:**
> I use no swap file at all with 2 GB of RAM. Swap is nice to have if you have a lot of applications open or for recovering when something goes wrong and all of your memory is used, but it is also very slow when it is being used. So, rather than have my swap partition be used when memory usage get high, everything will still stay in RAM. It means that hibernate doesn't work (you need swap space to hibernate) but I prefer a more responsive system.

And if you need hibernate to work, just make a swap partition and adjust the swappiness so that swap is not used so much. I always do this, I only really need swap for hibernation so I make my swap as large as my ram and turn down the swappiness. See [this]("http://ubuntuforums.org/showpost.php?p=1255511&postcount=43") page on how to do that.

---

### Post by fragos on 2009-03-02
> **damis648 said:**
> And if you need hibernate to work, just make a swap partition and adjust the swappiness so that swap is not used so much. I always do this, I only really need swap for hibernation so I make my swap as large as my ram and turn down the swappiness. See [this]("http://ubuntuforums.org/showpost.php?p=1255511&postcount=43") page on how to do that.

Same here. I found that for my work 1GB of memory was sufficient with swappiness=10 to almost never use swap space.

---

### Post by jpeddicord on 2009-03-02
> **damis648 said:**
> And if you need hibernate to work, just make a swap partition and adjust the swappiness so that swap is not used so much. I always do this, I only really need swap for hibernation so I make my swap as large as my ram and turn down the swappiness. See [this]("http://ubuntuforums.org/showpost.php?p=1255511&postcount=43") page on how to do that.

I used to use that, but there was a glitch in the jaunty kernel that threw everything into swap anyway. It's probably resolved, but I still like my swapless system. :D

---

### Post by emarkay on 2009-03-02
So rule of thumb (in general) is set the Linux Swap HD space to the amount of RAM installed and keep the default "swappiness"?

---

### Post by Crafty Kisses on 2009-03-02
Depending on how much RAM you have it may not even matter. A lot of people say make the swap partition double your RAM, but if you have like 1 or 2 gigs of RAM I wouldn't worry about it, if you have 512, then make it like 1024 or something.

---

### Post by absolutezero1287 on 2009-03-02
I have 2GB of RAM with a 1 GB swap. Its all I need.

---

### Post by Predtech on 2009-03-02
Sorry i never said that i use 8GB of DDR2 800 ram, but i also have other drives in my pc that total 1.75TB. So considering that i have a considerable amount of high performance RAM i could probably do away with SWAP???

---

### Post by darco on 2009-03-02
I went overboard on my mem cuz its so cheap...
8gigs of ram, 256mb of swap partition and swappiness set to 20.
When set to 0 or 10 it for some reason still went to swap even though I had oodles of cached ram????

darco

---

### Post by CoreyB. on 2009-03-02
Not to hijack the thread, but what if I have 3-4 GB of RAM, and use 64-bit.  How much swap should i use and still be able to use hibernate?  I don't do anything intensive, really.  Also, what should I set the swapiness to improve performance.  I don't really understand the swap file.

---

### Post by fragos on 2009-03-02
Rule of thumb for hibernation you need swap = to RAM size.

---

### Post by Predtech on 2009-03-02
I'm gonna use a Gparted live cd to shrink my swap drive to 1GB. I think with my 8GB's of ram that'll be fine. I checked how much ram is being used in the system manager, man i use absolutely no swap, lol.

---

### Post by absolutezero1287 on 2009-03-02
8 GB of RAM?!

Why would you even need a swap space? Unless you do some heavy gaming or work with media.

---

### Post by fragos on 2009-03-02
I think there's a 2nd part to the OP's question about how much swap space. Exactly how gracefully will the system handle running out of swap space?

---

### Post by Predtech on 2009-03-02
> **absolutezero1287 said:**
> 8 GB of RAM?!

Why would you even need a swap space? Unless you do some heavy gaming or work with media.

I shrank it down to 1.5GB, just in case, but i don't do any heavy media work at all except fro converting a few movies now and then for my ipod touch. I added the rest of the space to what's now an 85GB partition on which i Mac OS X installed.
It's nice to have all 3 major OS's running on 1 pc.

---

### Post by fragos on 2009-03-02
With 1GB RAM the most swap I've ever used is about 30KB and as rule none.

---

### Post by handy on 2009-03-03
I never create a /swap if I have 1Gb or more of RAM.

If a user is doing graphics intensive work with images, movies, CAD, 3D rendering or whatever then they may need swap, though if they are serious about that kind of work they would also have a heap of RAM anyway.

---

### Post by SuperCurro on 2009-03-08
I've got 1GB ram and when my 5 php webs are consulted at the same tame the RAM goes off over 1.3 GB ram. so I need the swap file. The problem is when I go over 300 mb swap, the ubuntu freezers. If I run Virtual Box and ask for the 5 php webs, the computer starts read hard disk and never finish (1 hour later).

Does someone have this problem?

---

### Post by fragos on 2009-03-08
You need more swap space. Rule of thumb is equal to installed RAM but you might need more swap on a server with a heavy load of mixed applications.

---

### Post by dcstar on 2009-03-08
> **emarkay said:**
> So rule of thumb (in general) is set the Linux Swap HD space to the amount of RAM installed and keep the default "swappiness"?

The only "rule" valid now is that if you want to use hibernation then your swap size must be (at least) as big as you physical RAM.

These days with more than adequate RAM available the need to go to swap (which is just a slowly performing extension of you RAM) is far far less than in the olden days of expensive RAM and cheaper hard drive space.

Systems with sufficient RAM for the processes in use can do without swap altogether and work quite happily (thank you very much....)

Systems that use SSD hardware and must have some swap (usually because of recalcitrant apps that refuse to let the OS do all the memory management) sometimes have a small swap partition created in a RAM disk.

---

### Post by dcstar on 2009-03-08
> **SuperCurro said:**
> I've got 1GB ram and when my 5 php webs are consulted at the same tame the RAM goes off over 1.3 GB ram. so I need the swap file. The problem is when I go over 300 mb swap, the ubuntu freezers. If I run Virtual Box and ask for the 5 php webs, the computer starts read hard disk and never finish (1 hour later).

Does someone have this problem?

Your problem is not insufficient swap, it is insufficient RAM.

---

