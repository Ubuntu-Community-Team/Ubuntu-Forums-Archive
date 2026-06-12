---
title: "Doom framerate stumbles"
date: 2010-03-17
forum: Gaming &amp; Leisure
---

### Post by Paradox Uncreated on 2010-03-17
Hi. I'm running Doom 3 and the framerate stumbles. Is there a jitter issue somewhere, that can be configured, or anything similar?

---

### Post by glaze on 2010-03-17
What's your graphics card? Have you updated Doom3 to the latest version?

---

### Post by Paradox Uncreated on 2010-03-17
gtx 280. I'm running the latest version from ftp.

---

### Post by Paradox Uncreated on 2010-03-17
Uneven framerates when ghouls are a-jumping, that's no good.

Let me tell you what I did.

First of all, here is the hardwarelist, atleast the one I got in opensolaris, when I tried that.

[IMG]http://www.paradoxuncreated.com/Pxu/device_driver_utility[/IMG]

I installed -ck patch, set hz to 300, and full preemption.
I did, echo "2" > /proc/sys/kernel/rr_interval

I used top, and tweaked the priority of doom3 to -13
I also installed irqbalance.
I run with sync to vblank on, and flipping off. (Seems to work better with flipping off.)

I have an AutoExec.cfg, in .doom3, with:

seta image_lodbias "-0.5"
seta image_filter "GL_LINEAR_MIPMAP_LINEAR"
seta com_showFPS "1"
seta com_fixedTic "-1"
seta com_PreciseTic 0
seta com_allowConsole

These are the tweaks I have done so far. But I'm still having problems with stumbling framerates.
I would expect the framerate to be firmly at 75hz, when running it 640x480 windowed. (Since that is my LCD refresh rate).
However it is not.. And the same framerate problem is evident, when running it at 1280x1024. So reducing the resolution does not help. There must be a bottleneck somewhere.

---

### Post by Paradox Uncreated on 2010-03-17
I googled a bit around, and it seems that the linux binaries are not as optimized as they could be. Nothing much to do about it?

---

### Post by lateralus-paradox on 2010-03-17
Yea, I doubt there's much you can do if it's an operating system problem. A framerate drop that's caused by bad programming will usually never go away unless they develope a patch for it. I used to get really bad framerate drops with Call of Duty Modern Warfare playing on Winblows, and I could never fix the problem. But with Linux/Ubuntu, a patch or fix could be a relatively short wait away.
 
What I'm really interested in is, how does one go about installing Doom 3 to a machine runnig Ubuntu (my version is Ubuntu 9.10 Karmic Koala). If you could just post the process you used to do that, I'd much appreciate it.
 
Thanks.
lateralus-paradox

---

### Post by Paradox Uncreated on 2010-03-17
> **lateralus-paradox said:**
> Yea, I doubt there's much you can do if it's an operating system problem. A framerate drop that's caused by bad programming will usually never go away unless they develope a patch for it. I used to get really bad framerate drops with Call of Duty Modern Warfare playing on Winblows, and I could never fix the problem. But with Linux/Ubuntu, a patch or fix could be a relatively short wait away.
 
What I'm really interested in is, how does one go about installing Doom 3 to a machine runnig Ubuntu (my version is Ubuntu 9.10 Karmic Koala). If you could just post the process you used to do that, I'd much appreciate it.
 
Thanks.
lateralus-paradox

It's in the archive file, just run it with sh. Additional information for steam version is here, aswell: [http://n3wt0n.com/blog/?p=745](http://n3wt0n.com/blog/?p=745)

I've been thinking about the possiblity of tuning IRQ priorities to improve the performance though.

---

### Post by dfreer on 2010-03-17
> **lateralus-paradox said:**
> 
What I'm really interested in is, how does one go about installing Doom 3 to a machine runnig Ubuntu (my version is Ubuntu 9.10 Karmic Koala). If you could just post the process you used to do that, I'd much appreciate it.
 
Thanks.
lateralus-paradox

[http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/)

---

### Post by Paradox Uncreated on 2010-03-17
So... We have a set of values.

First of all, PCI latency timer in BIOS, higher = more performance. Lower = (?)
I set it to max in the BIOS, and my audio still can play at 0.363 ms latency. So this setting alone does not affect low latency performance.

Next.. setpci, lspci.. priorities and latencies. What needs what and how much, or something along those lines.

lspci -v 
hmmm ok, a lot of stuff is latency 0 here, I don't know what that's about. Probably not something I should touch.
The only device that actually was set to 248, was the firewire device, which is my firewire audio card, which worked excellently anyway.
I can try setting the gfx card higher, since I read that "many gfxcard manufacturers set their latency higher, to look better in benchmarks".
sudo setpci -v -s '03:00.0' latency_timer=96
That did also not hurt low-latency performance.
Not really sure if it helped doom3. It does perform quite well, but there seems to be some kind of timing issue. You have a couple of smoothflowing frames, and then it seems to skip a few frames, for a a few more smooth frames.

Then we have priorities..  I followed some information on FFADO site, but it doesn't seem to apply to my machine, apparently theres just some softirq stuff running here.

Next, nicing, all applications could be nice to doom3, I think.. or does doom3 rely on that some services have some priority?
sudo gnome-terminal &
and then top, in the root console.

opening up doom3 in windowed 640x480 mode.
renicing with r in top. -13 might be a good value.

This is just based on my guesswork though. If there is any experts here, please chime in.

---

### Post by lateralus-paradox on 2010-03-17
> **Paradox Uncreated said:**
> It's in the archive file, just run it with sh. Additional information for steam version is here, aswell: [http://n3wt0n.com/blog/?p=745](http://n3wt0n.com/blog/?p=745)

or

> **dfreer said:**
> [http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/)

weren't all that helpful in my case. I should have specified that I needed to know how to do it with the retail versions of the CDs. My bad. I found this pretty good tutorial here

[http://www.ubuntumagazine.net/?p=1183]("http://www.cyberciti.biz/faq/linux-install-doom3-game/")

and it seems to have worked fine. Thanks for the help anyways guys. :P

---

### Post by Paradox Uncreated on 2010-03-18
I guess this is when we bring out the optimizing binary reassembler.

---

### Post by Brebs on 2010-03-20
For [doom3 smooth in single-player](http://forums.gentoo.org/viewtopic.php?p=4014247#4014247):

set com_fixedtic 1
set com_syncgameframe 1

Note that this is 60 frames-per-second, *not* 75.

---

### Post by Paradox Uncreated on 2010-03-21
I think I actually fixed the problem. I recompiled the kernel with some additional preemption, (rcu).

And also I enabled some optimizations that seemed harmless: -w -march=native -O2 -pipe -fomit-frame-pointer -mfpmath=sse,387 -fgcse-lm -fgcse-sm -fgcse-las -fgcse-after-reload -fpredictive-commoning  -ftree-vectorize -fvect-cost-model -floop-optimize -fivopts -freorder-blocks-and-partition -ftracer -fbranch-target-load-optimize -fbranch-target-load-optimize2 -fbtr-bb-exclusive -fmodulo-sched -fno-branch-count-reg -ftree-loop-linear -fmodulo-sched-allow-regmoves -fsee -floop-interchange -ftree-loop-distribution -ftree-loop-im

Peace Be With You.

---

