---
title: "How Much Mem Do I need?"
date: 2011-03-17
forum: Desktop Environments
---

### Post by Rasputin69 on 2011-03-17
I have a 1 Gb ram system.

I haver periodic freezes.

I am guessing this is a ram issue.

How much do I need.

I am considering a new PC.

How much RAM can Ubuntu 10.10 Meerkat take advantage of?

---

### Post by Drone4four on 2011-03-17
Meerkat 32bit can take advantage of less than 4GBs of ram.  Meerkat 64bit can take advantage of any amount of ram.  To answer your question, how much memory do I need, first you have to tell us what you will be doing with your new PC.  For example, video editing, gaming, word-processing or just surfing the world wide web?

---

### Post by Rasputin69 on 2011-03-17
I will be buying a state of the art 64 byte system.
 and have allocated a budget of up to $ 700.00 but will save what I can so I will take advantage of high mem. I will have the ram installed on the dateof purchase  by the vendor.

My use is for MoneyDance (Quicken like financial software) some databases kept in Base with Calc as a front end, email and Internet using Chrome.

I process some still photos but do not use video processing.

---

### Post by asmoore82 on 2011-03-18
> **Drone4four said:**
> Meerkat 32bit can take advantage of less than 4GBs of ram.
You can install the -PAE ([[COLOR="Purple"]Physical Address Extension[/COLOR]]("http://en.wikipedia.org/wiki/Physical_Address_Extension")) kernel variant
to use over 4GB of RAM on 32-bit.

> **Rasputin69 said:**
> I have a 1 Gb ram system.

I haver periodic freezes.

I am guessing this is a ram issue.
Naturally more is better, but 1GB of RAM should be plenty for general desktop use.
RAM should only be the bottleneck if you are doing extreme photo editing,
Virtualization of multiple OS's, or heavy development work.

My work laptop has 8GB, but my home desktop still has
only 512MB and never has any freezing issues.

---

### Post by Krytarik on 2011-03-18
For comparison: I have 1.2 GB RAM installed currently, running full Ubuntu 10.04 with Gnome/Compiz, and the memory usage generally doesn't exceed 50%.

But if I were about to buy a new machine, I would choose 4 GB RAM currently. And I recommend buying at least 2 GB RAM.

Greetings.

---

### Post by mcduck on 2011-03-18
> **Rasputin69 said:**
> I have a 1 Gb ram system.

I haver periodic freezes.

I am guessing this is a ram issue.

How much do I need.

I am considering a new PC.

How much RAM can Ubuntu 10.10 Meerkat take advantage of?

1GB should be plenty for Ubuntu unless you use virtualization software or other really memory hungry tasks. I have 1GB and use the machine for 3D graphics (probably lot heavier than what you are doing) and I'm rarely even using all that RAM.

But why guess, when there's an easy way to check if lack of RAM might be causing your problems. When the computer is freezing, pop open a terminal and run "free -m". Check the "-/+ buffers/cache"-line and the amount of swap used (if any). Post the info here if you need help interpreting it.

(If I remember correctly, the 64-bit Ubuntu kernel is configured to support up to 64TB of RAM. That's definitely more than you could possibly fit into your computer, so you don't need to worry about running to any limit three... :D)

---

### Post by 3Miro on 2011-03-18
Here is my view:

512MB - minimum (Ubuntu can work on less, but it becomes tricky to setup a stable system)
1GB - smooth
2GB - comfortable (I would also call this the minimum if you want to play wine games or use Virtual Box)
4GB - sufficient (this is enough for almost all tasks)
8GB - powerful (unless you are running something very special, you will not need more than this)

For less than 3GB, I would recommend 32-bit system, for more than 3GB I would go with 64-bit (unless you have an issue with printer drivers or very weak CPU).

Those are my recommendations, so they should not be taken as "absolute" or "official".

---

### Post by xerman on 2011-03-21
> **3Miro said:**
> Here is my view:

512MB - minimum (Ubuntu can work on less, but it becomes tricky to setup a stable system)
1GB - smooth
2GB - comfortable (I would also call this the minimum if you want to play wine games or use Virtual Box)
4GB - sufficient (this is enough for almost all tasks)
8GB - powerful (unless you are running something very special, you will not need more than this)

For less than 3GB, I would recommend 32-bit system, for more than 3GB I would go with 64-bit (unless you have an issue with printer drivers or very weak CPU).

Those are my recommendations, so they should not be taken as "absolute" or "official".

Actually, get as much memory as your budget allows you, always depending on the maximum memory motherboard is capable of installing. I would go always with no less than 2 GB. If video card is onboard and address 512 Mb to video in BIOS (maximum in all motherboards I've been using), I would rather go to 4 GB, leaving 3.5 for the system and 0.5 for the video card.

Then while installing adjust swap file. You could also get rid of swap file, though system installer complains, can do, and you will be using only physical memory, not hard drive as memory. This should make system faster.

Actually, issues with today's computers deal more with memory than with processor speed for common tasks. Video/audio editing, molecular analysis, complex calculations take advantage of processor speed and 64 bit.

I always go to 64 bit OS because 64 bit processors have been around for quite a while now, and 64 bit OS should be standard. Though benefits of using 64 bit OS apply just to certain apps.

Anyway, it is important that motherboard is capable of installing memory up to, let's say 16 GB, then you could start with 2 GB and add memory if you need more. Adding memory is always easier than changing processor.

Regards
Xermán

---

### Post by n.williams0440 on 2011-03-21
Thanks for the sharing...

---

### Post by mcduck on 2011-03-21
> **xerman said:**
> 
Then while installing adjust swap file. You could also get rid of swap file, though system installer complains, can do, and you will be using only physical memory, not hard drive as memory. This should make system faster.


Not having a swap partition will not make your computer faster.

Actually the only thing you benefit from doing that is saving a bit of hard drive space (at the expense of loosing the ability to suspend the machine, and getting a nice "out of memory" error if you try to do something that would require more RAM than what you have...)

The operating system will only use swap if it really needs to, not just because it's there. :D

---

### Post by KegHead on 2011-03-21
Hi!

I run 2gb on all of my machines w/no problems. 

10.10 & 9.04 testing 11.04.

KegHead

---

### Post by walt.smith1960 on 2011-03-21
> **mcduck said:**
> Not having a swap partition will not make your computer faster.

Actually the only thing you benefit from doing that is saving a bit of hard drive space (**at the expense of loosing the ability to suspend the machine,** and getting a nice "out of memory" error if you try to do something that would require more RAM than what you have...)

The operating system will only use swap if it really needs to, not just because it's there. :D

You can suspend without any swap at all, I've done it.  You cannot **hibernate** without a swap partition; a swap file is not adequate.

---

### Post by mcduck on 2011-03-21
> **walt.smith1960 said:**
> You can suspend without any swap at all, I've done it.  You cannot **hibernate** without a swap partition; a swap file is not adequate.

Well, I should probably added the "-to-disk" part to suspend.

Anyway, I meant ACPI S4, AKA "Suspend to Disk",or like you said, "hibernate". Suspending to RAM of course doesn't require a swap partition.

But anyway the point was that not having a swap partition will not increase your performance in any way, it only gains you a bit of extra hard drive space.

---

### Post by Krytarik on 2011-03-21
+1 for not sparing the swap partition. You don't know when you will eventually need it, and like *mcduck* said, it doesn't negatively affect the OS' performance.

---

### Post by fatriff on 2011-03-21
These days the graphics card is the all important factor, it handles allot of the tasks the cpu used to.

Crap graphics card = crappy slow machine.

---

### Post by cmileto on 2011-03-21
Ram is more important than video card.
Put a $500 geforce in the machine and its still gonna suck the balls if you have too low ram and its swapping and thrashing the HD.

Ram is the single best investment you can make as far as computer speed goes. Next is CPU, though today about any dual core is good for about anything.

As far as video unless your building a machine for gaming or you need to use the VPU for calcs you can get  awesome compiz effects with a fairly meager vid card. The majority of motherboard integrated nvidia (somewhere around the 6000 series and up) and some ati integrated (somewhere around 2400 HD and up) video cards are more than capable of running compiz with high res and settings cranked. And they will still play Doom3 in wine at 1024 by 768 with settings up

---

### Post by nevius on 2011-03-21
> **Rasputin69 said:**
> 
I haver periodic freezes.


What do you mean when you say that you 'have periodic freezes'? Do you mean that your computer will randomly crash for no particular reason? Does it periodically run slowly? I know you wrote that you have 1 GB of RAM. What are the other components in your computer (ie processor or graphics card)?

Of course, we could always try not to help you so that you have a better reason to get a new computer? :) Everyone likes a new computer. :)

---

