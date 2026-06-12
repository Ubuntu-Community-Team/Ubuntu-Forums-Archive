---
title: "KDE vs GNOME memory consumption?"
date: 2007-04-23
forum: Desktop Environments
---

### Post by Hashi on 2007-04-23
Hi,
  I installed feisty Kubuntu, 'cause I prefer KDE over GNOME, just a personal thing. For various reasons, I also installed Gnome-Desktop, so that I can select either environment when I start up. Funny thing - KDE, with nothing else running (I think - I certainly haven't manually started anything anyway) consumes approx 800Mb of my 1Gb memory. Running any apps causes this to increase rapidly. However, running GNOME, it only consumes about 200Mb, and starting apps doesn't seem to cause as much memory consumption.
  What gives? Is KDE really that memory hungry? Should I be concerned? 
Also, there are various things that DO work under GNOME, but not KDE, for instance my wireless card, aot plug of USB devices amongst others.
  Has anyone else run into these issues, or is it just me? Thanks,
Hashi.
PS I won't bore you with my hardware details unless requested, I don't think they are relevant, but I could be proved wrong!

---

### Post by simonn on 2007-04-23
IMHO Gnome and KDE are both memory hungry anf flabby for not a lot of gain. Use XFCE - with Xubuntu.

---

### Post by Hashi on 2007-04-23
Thanks, you know I think I will try it. It's just that the "big two" get so much air time that I kinda forgot there are alternatives available.
Hashi.

---

### Post by firephoto on 2007-04-23
If you're judging by the KDE System Guard it doesn't report the total memory used accurately.

---

### Post by No Whammies on 2007-04-23
How about KDE used with Dolphin?  Would that use less memory?

---

### Post by wdaniels on 2007-04-24
> **firephoto said:**
> If you're judging by the KDE System Guard it doesn't report the total memory used accurately.

This is the problem - no way KDE is using 800M straight after boot!  Linux tends to use up any available memory for cache and just dumps it as required when it's needed for apps. KSysGuard includes all those buffers in it's figures so you can't really see from that. You could use the command "free -m" in a terminal and check the numbers on the "-/+ buffers/cache" line to see the real usage.

Between KDE and GNOME, memory usage may depend on which and how many apps you tend to use. I expect KDE will be using a bit more RAM initially, but because KDE apps tend to be reusing a lot of the same libraries it could end up being less.  But if you still use FF, Evolution, OO etc. then that wouldn't really make a difference.

---

### Post by phenest on 2007-04-25
I just have to say: does it really matter how much memory they're using? What would be the point of having memory installed in your computer if you don't want it to use it? Besides, memory usage is not down to KDE or Gnome. Memory management is handled by Linux itself and it does it very well. The only time you need concern yourselves with this is when you have used all your swap too.

---

### Post by rillip on 2007-04-25
For comparison's sake, my Kubuntu system, with 512 mb of Ram, is using 510 with Opera, KTorrent and the System Gaurd runnig.  I think what you're seeing is specific to your situation rather than an overall memory usage issue by KDE, though I won't make any claims as to its relative performance.

---

### Post by simonn on 2007-04-25
> **phenest said:**
> I just have to say: does it really matter how much memory they're using? What would be the point of having memory installed in your computer if you don't want it to use it?

You have a point, however, free memory in linux is often not really free, but is being used for buffers and cache. So, the more "free" memory you have, up to a point, the faster your computer will be.

> Besides, memory usage is not down to KDE or Gnome. Memory management is handled by Linux itself and it does it very well. The only time you need concern yourselves with this is when you have used all your swap too.

Memory usage is, to a certain extent, down to KDE and gnome. They run as series of processes which take up memory. XFCE performs a similar function to KDE and gnome, but uses less memory doing it.

---

### Post by oobuntoo on 2007-04-26
Unused memory is wasted memory, in my opinion. Big portion of used memory report by Ksysguard is cached memory. This is done for performance reason. If a newly started app needed memory, part of the cached memory would be free right away. As long as it's not a result of a memory leak, I would not worry too much about what ksysguard reported, unless your system is really running slow.

What is the point of having 50% of your memory free all the time? Use what you paid for. That seems to be memory management design philosophy these days, even for Windows Vista.

---

### Post by orb9220 on 2007-04-26
And the other thing to consider on these type of issues. 

"Well my desktop is slowing down when I have 9 apps open on all the sides of my Cube. And ram shows 85% used,"

"Well what video card are you using?"

" nvidia Gblah blah with 64mb"

That is alot of slow down on the desktop. Implementing Advance features on a legacy video card,

I start to see problems when I have more than 6 High requirement apps on my FX-5200 128mb card.

Like Ktorrents,Amarok,Firefox,OpenOffice etc... on my gnome desktop.

---

### Post by Eric Layne on 2007-04-26
> **oobuntoo said:**
> Unused memory is wasted memory, in my opinion.

This is the first time in my life I have seen someone refer to free memory as 'wasted memory'.

---

### Post by wdaniels on 2007-04-26
> **oobuntoo said:**
> Unused memory is wasted memory, in my opinion.

That all depends on what memory is being used for.  In the case of cache buffers then any unused memory is wasted since these buffers can be freed as readily as they are allocated - I don't think anybody is disputing that, it's merely a cause of confusion for people not familiar with linux.

But that is not necessarily the case for memory consumed by the "base" desktop environment since that cannot freed so readily (if at all).  So the issue is not entirely moot.  For example, I have 1Gb RAM so 90% of the time it wouldn't really matter if my DE is hogging 200 or 400 Mb to provide basic DE functions, but when I occasionally launch Anarchy Online, it does matter all of a sudden.  Not because the linux kernel can't or is reluctant to swap most of my DE onto disk while I play the game, but because I find having more free physical RAM available for the kernel to use as disk cache vastly improves the performance of the game.  If I happen to have a few background apps running that I'm reluctant to close (e.g. for torrents or music) then these processes, and the parts of the DE they use, can't just be completely swapped out onto disk.

Efficiency in terms of memory consumption by each DE may not be a primary consideration if you have RAM to spare, but it is not entirely irrelevant or undesirable as some here seem to be suggesting.  I believe the poster here asked a valid question, despite the initial confusion with KSysGuard.

---

