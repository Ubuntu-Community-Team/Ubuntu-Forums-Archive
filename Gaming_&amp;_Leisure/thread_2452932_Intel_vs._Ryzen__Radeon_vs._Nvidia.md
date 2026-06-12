---
title: "Intel vs. Ryzen / Radeon vs. Nvidia"
date: 2020-10-30
forum: Gaming &amp; Leisure
---

### Post by Shibblet on 2020-10-30
I want to build an AMD Ryzen 5000 with Radeon 6800XT Video Card PC.
Will there be any compatibility issues with Linux, or Kubuntu in particular?

I have been told that AMD Graphics Cards work better than Nvidia Graphics cards with Linux, because of the driver support.

I have also been told that it took quite a while for Linux Kernel updates to actually support the Ryzen 3000 series processors.
Will this be similar with the Ryzen 5000's ?

Is any of this stuff true?  I am in research mode right now, and will probably purchase and build my new PC around March.

---

### Post by DuckHook on 2020-10-30
I use AMD in my main box, but it's 8 yrs old at this point. My anecdotal experience is not much to go on, I'm afraid.

A brief scan of the forums indicates that either OEM is acceptable, but it's actually Intel&#8209;based cards/GPUs that give the least trouble.

The primary takeaways seem to be:

[LIST=1]
[*]Avoid cards that are either too new or too old.
[*]Avoid cards that are overly specialized, powerful or esoteric.
[*]Stick with the mainstream and things tend to go smoothest.
[/LIST]
Observe the above and all three OEMs look okay.

---

### Post by CatKiller on 2020-10-30
> **Shibblet said:**
> I have been told that AMD Graphics Cards work better than Nvidia Graphics cards with Linux, because of the driver support.

I'm just going to repost this from two days ago:

> **CatKiller said:**
> You may have heard that, but it isn't true.

The Nvidia Linux driver is essentially the same as the Nvidia Windows driver, but made to work on Linux. You get the same performance and day-one hardware support as you'd get in Windows, and it has some fundamental weirdnesses because it's really a driver from a different operating system, and no one other than Nvidia can ever fix it because it's proprietary. 

The AMD driver is open source, and part of the kernel/Mesa, so it plays nicer with everything else. They used to have a proprietary driver, too, but it was absolutely terrible so they dumped it. They don't have the resources to get everything lined up before hardware is released, so initial support goes into the versions of the kernel and Mesa that are released after the hardware, then there's a polishing period, and eventually good hardware support will trickle down to the distros. Users with AMD hardware will feel much more incentive to run a rolling-release distro or add PPAs with newer versions of Mesa to speed up the trickling. Because the driver is open source, other people can put in things that are important to them: Valve swapped out the shader compiler, as an example. 

Either approach could be regarded as great or woefully inadequate, depending on your point of view.

Nvidia in laptops is just terrible, though. Don't attempt that.

---

### Post by oldfred on 2020-10-30
Not sure if Phoronix has newer comparison or not:

20-Way GPU Gaming Comparison With March 2020 Linux Drivers
[https://www.phoronix.com/scan.php?page=article&item=march-2020-gaming&num=1](https://www.phoronix.com/scan.php?page=article&item=march-2020-gaming&num=1)

---

### Post by mastablasta on 2020-11-02
these are very new CPU and GPU chips. some are not even out yet. for AMD there is already kernel support, but you need the very latest kernel. and even there support might still be limited rather than full.

you will need to manually install newer mainline kernel and also maintain updates manually. 

perhaps a temporary jump to Manjaro is in order until appropriate kernel gets to Kubuntu.

---

