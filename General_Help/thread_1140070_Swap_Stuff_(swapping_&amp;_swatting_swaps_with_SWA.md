---
title: "Swap Stuff (swapping &amp; swatting swaps with SWAT)"
date: 2009-04-27
forum: General Help
---

### Post by Th3Professor on 2009-04-27
Okee dokee, it was recommended I split up a ton of questions I had somewhere else into different threads (that cover multiple topics). Here are some of 'em...

I have 5 hard drives:
1= OS (all boots and primary system files)
2,3,4= storage (raid5 & lvm)
5= external (movable storage)

My partitions:
sda1,2,3,5,6,9,10 = OS stuff/storage/etc.
sda7 = swap (striped priority with sda8 )
sda8 = swap (striped priority with sda7)
sdb1,c1,d1 = raid5 & lvm
sdi1 = external drive

Swap ?s:

[LIST=1]
[*] I think that I can use the 2 swap spaces (sda7, sda8 ) concurrently with solaris (not just linux). Is that right?
[*]That would be excellent if sysv will recognize my current linux swaps. However, do I need separate swap space set aside to work with bsd?
[*]Other linux installs will recognize and use my current swap spaces, right?
[*]Is it possible to have either linux and/or sysv and/or bsd use swap space that is reserved on my raid5 & lvm set-up (sdb, sdc, sdd)?
[*]Why is it that even when my RAM peaks in usage that I still use minimal (like maybe 0.5%) swap?
[*]I have 4GB RAM, so I set up "2x2GB" swaps with equal/shared priorities (striped), instead of "1x4GB swap". I read that striping swap space can be useful so went ahead and went for it, though am not really sure if it's even making a difference. Does it make a difference?
[*]As it is I'm hardly even using swap anyway, it seems useless even on my system's "heaviest" days. There are ideas on using X amount of swap for Y amount of RAM in order to produce "more efficient" results, and yet there are several opinions on just what amount is ideal. Why is that?
[/LIST]

---

### Post by cariboo on 2009-04-27
You only need 1 swap partition. I have had at various time three different distributions using the same swap partition.

---

### Post by Th3Professor on 2009-04-28
> **cariboo907 said:**
> You only need 1 swap partition. I have had at various time three different distributions using the same swap partition.

Thank you for your reply.

Going all swap crazy might turn someone into a swapzi (swap nazi) or something lol so to maintain my swapanity (swap sanity) ;) I'll sort this out a little better...

_**Number of swaps:**_

Why would some sources say use 2 swaps with shared/equal priorities (in a "striped" fashion)?

What might be a potential advantage to using that alternative over the standard 1 swap?

I've always used only 1 swap, though after I built the current computer I'm using and started researching raid options and lvm I ran into some sources that encouraged using 2 striped swaps (I think they may have mentioned it be even better if putting the 2 swaps on different physical disks). Perhaps it works well with raid, I don't know. But this is a first time for me to double it up.

_** Amount of swap:**_

I have 4GB RAM, or I am supposed to (I lose some, less than 100MB, on boot for some reason). I have approximately 4GB. Is that a good amount? Maybe more/less swap?

I just checked my ram & swap usage, and for the first time I am seeing a much larger amount of swap being used. It's usually such a small amount that I wonder if I need 4GB swap but right now I'm thinking maybe it's a good idea, or maybe even more. Not sure.

The GUI "System Monitor", in the "Resources" tab, lists the following:
Memory: 2.6 GiB (67.5%) of 3.9 GiB
Swap: 1.5 GiB (40.0%) of 3.7 GiB

The weird thing is, the terminal says otherwise:

```

             total       used       free     shared    buffers     cached
Mem:          3959       3904         55          0        441        791
-/+ buffers/cache:       2672       1287
Swap:         3812       1524       2287

```So I checked gkrellm:
Mem: 3960M - 1522M free
Swap: 3812M - 2287M free

And I checked conky:
ram: 2.61GiB/3.87GiB (67% used)
swap: 1.49GiB/3.72GiB (39% used)

That's a bunch of different readings. I'm sure there will be slight variations as apps open/close or are used more/less, though mismatching amount used/free between different monitor programs isn't so much of a concern as actual amount *available*.

Comparing those 3 monitor apps:
RAM available = 3.9 gigs, or 3959 megs, or 3960 megs, or 3.87 gigs (approx. 3870 megs)
Swap available = 3.7 gigs, or 3812 megs, or 3812 megs, or 3.72 gigs (approx. 3720 megs)

Regarding that lost RAM, after I boot, after bios, and during linux's loading and messages scrolling by, I receive (every time) a message that says I'm losing some of my RAM. I think it's says it's around 40 megs lost, which makes sense looking at some of the readings I listed above, yet I don't know why I am losing that memory.

Any ideas? Or how can I get it back?

(I know it's not much but that's still pretty weird, it doesn't seem like it's supposed to be lost, especially considering the warning/notification message at every boot. And, I've never seen that on other systems/computers.)

It's also odd that one application says I have approx. 3960 megs memory available but another application says I have approx. 3720 megs memory available. Putting the initial 40meg loss aside, that's a difference of about 240 megs. There's a similar difference in readings on available swap too.

How do I know which application is more accurate or actually correct?

_** Swappiness:**_

Another thing about swap, which I didn't mention in the OP, is swappiness. I haven't messed with my swappiness yet (or may not at all). 

It appears to be a priorities thing between ram and swap, or is it something else?

What are the pros/cons to a high or low swappiness setting?

Here are my current general priorities for swap from the fstab:
```

# /dev/sda7 none            swap    sw              0       0
# /dev/sda8 none            swap    sw              0       0

```My swappiness is currently:
```

$ cat /proc/sys/vm/swappiness 
60

```I think 60 is default. Not sure if I should bother changing it.

One could ask, "what's the purpose in your computer?" And it's basically multimedia, including gaming occasionally, lots of movies/tv shows, but also intent on use with a home recording studio (using Ubuntu Studio). (CPU is a 64-bit quad core, GPU is nvidia gtx260, not sure if sharing that is necessary in this case, but I do occasionally get "resource heavy", or use demanding apps, or use several apps simultaneously.)

_** Swap on other OS:**_

I'm glad that the swap I use on one Linux system will also be used on another Linux system. Elsewhere, someone mentioned considering separate swaps if using hibernation in one system and booting into another system. Though, I've always had bad luck with hibernation (after going back into that system something quirky happens, be it with audio or something else).

Would the same swap that I'm using with Linux also be used with Solaris?

Would the same swap also be used with OpenBSD?

My guess is yes to both sysv and bsd unix systems, but just double-checking.

_** Using swap on disk groups:**_

Are there any advantages or disadvantages to using swap on a group of disks, such as my "sdb, sdc, sdd" raid5/lvm set-up?

I may have read somewhere that it's useful with striping/parity disk set-ups like raid5, possibly including the earlier mentioned multiple striped swaps with shared priorities. That aspect of options for disk usage is a little confusing.

Thanks! :-)

---

### Post by Th3Professor on 2009-04-29
bump

---

### Post by Th3Professor on 2009-05-01
bump

---

### Post by Th3Professor on 2009-05-02
3rd bump

---

### Post by dcstar on 2009-05-02
> **Th3Professor said:**
> 
.......
[*]As it is I'm hardly even using swap anyway, it seems useless even on my system's "heaviest" days. There are ideas on using X amount of swap for Y amount of RAM in order to produce "more efficient" results, and yet there are several opinions on just what amount is ideal. Why is that?
[/LIST]

Summary: There is (still) and incredible amount of BS about swap around - most of it is basically "ancient history" that has little relevance in these days of large amounts of RAM available in systems. The only common need for swap in (most) systems at the moment is for hibernation otherwise you are just using up disk space.

30+ years ago a lot of people started their cars on cold mornings and wasted a lot of fuel waiting for them to warm up, they no longer do that because the technology changed. 10 years ago people still used a lot of swap because RAM was expensive, they **should** no longer do that because technology has changed - but some still advocate old swap myths.

---

### Post by Th3Professor on 2009-05-03
Thank you for your reply.

Moving on to the other questions, so far I've had responses to # of swaps... one person said only need 1 swap partition, one person said should need 0 swap space (or very little perhaps, it was a little unclear)

My previous questions still stand...

_**Number of swaps:**_

Why would some sources say use 2 swaps with shared/equal priorities (in a "striped" fashion)?

What might be a potential advantage to using that alternative over the standard 1 swap?

_**Amount of swap:**_

I have 4GB RAM. I have approximately 4GB swap. Is that a good amount? Maybe more/less?

[U][B]Regarding that lost RAM:

[/B][/U]...after I boot, after bios, and during linux's loading and messages scrolling by, I receive (every time) a message that says I'm losing some of my RAM. I think it's says it's around 40 megs lost, which makes sense looking at some of the readings I listed above, yet I don't know why I am losing that memory.

Any ideas? Or how can I get it back?

Also... one application says I have approx. 3960 megs memory available...
...another application says I have approx. 3720 megs memory available...
...there's a similar difference in readings on available swap too.

How do I know which application is more accurate or actually correct?

_** Swappiness:**_

What are the pros/cons to a high or low swappiness setting?

_**Swap on other OS:**_

Would the same swap that I'm using with Linux also be used with Solaris?

Would the same swap also be used with OpenBSD?

_**Using swap on disk groups:**_

Are there any advantages or disadvantages to using swap on a group of disks, such as my "sdb, sdc, sdd" raid5/lvm set-up?


Thanks! :-)

---

