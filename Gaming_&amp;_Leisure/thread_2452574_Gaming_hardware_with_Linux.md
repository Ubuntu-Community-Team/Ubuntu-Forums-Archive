---
title: "Gaming hardware with Linux?"
date: 2020-10-24
forum: Gaming &amp; Leisure
---

### Post by lillyflower on 2020-10-24
Hello. What can you recommend of the best hardwares to gaming in Ubuntu? I would like to game Rdr2, Terraria, Minecraft and hopefully I can play newer popular games in Ubuntu with good graphics in the future. I heard AMD support more than NVIDIA in Ubuntu? I was thinking earlier get a laptop but now I want a desktop.

---

### Post by TheFu on 2020-10-25
If your budget is $4000, you won't have any problem. Get a Core i9 with 64G-128G of RAM and the most expensive AMD GPU you can get.
Are you building the system on your own? Then you can ensure the components are compatible and don't have to deal with funky OEM BIOS stuff.
Be certain to get a good quality PSU with the efficiency and power output needed. From year to year, the most reliable PSUs change. I have a Corsair and a number of Seasonic PSUs.  For storage, probably want a few Samsung NVMe 970 Pro SSDs.

On the high-end, nvidia GPUs are better, but then you are stuck with whatever nVidia decides to support and when they decide to stop.

If your budget is more modest, say only $3000, you might be able to get by with lessor hardware.

Of course, the rest of us can go really cheap and make lots of compromises because price matters more.  I reuse lots of parts from my current systems and buy just 3-4 items - MB, CPU, RAM, and perhaps a GPU.  My next GPU will probably be an nVidia 710 with quad-HDMI output.  [https://www.phoronix.com/scan.php?page=article&item=asus-50-gpu&num=1](https://www.phoronix.com/scan.php?page=article&item=asus-50-gpu&num=1) explains some reasons for preferring that GPU. There are other articles at that link about gaming systems too.

---

### Post by jcdenton1995 on 2020-10-27
I'm actually looking at buying a graphics card right now so I'm also interested in this. I was leaning towards a AMD RX5700 XT basically because it's in my price range and I want a really mainstream card that will be well supported that can run games that are at least a couple of years old at 4K resolutions, and use 2K for the rest. I don't suppose there are any pitfalls to consider when using a well established distro like Ubuntu 20.04 LTS?

I would get into the minutiae of it if I had the time, but I already spend a lot of time just learning about Linux in general, which I fell is more valuable to me at the moment than getting into the nitty gritty of graphics cards, I just need something that works either out of the box, or with a reasonable amount of tweaking!

---

### Post by CatKiller on 2020-10-27
> **lillyflower said:**
> I heard AMD support more than NVIDIA in Ubuntu?

You may have heard that, but it isn't true.

The Nvidia Linux driver is essentially the same as the Nvidia Windows driver, but made to work on Linux. You get the same performance and day-one hardware support as you'd get in Windows, and it has some fundamental weirdnesses because it's really a driver from a different operating system, and no one other than Nvidia can ever fix it because it's proprietary. 

The AMD driver is open source, and part of the kernel/Mesa, so it plays nicer with everything else. They used to have a proprietary driver, too, but it was absolutely terrible so they dumped it. They don't have the resources to get everything lined up before hardware is released, so initial support goes into the versions of the kernel and Mesa that are released after the hardware, then there's a polishing period, and eventually good hardware support will trickle down to the distros. Users with AMD hardware will feel much more incentive to run a rolling-release distro or add PPAs with newer versions of Mesa to speed up the trickling. Because the driver is open source, other people can put in things that are important to them: Valve swapped out the shader compiler, as an example. 

Either approach could be regarded as great or woefully inadequate, depending on your point of view.

Nvidia in laptops is just terrible, though. Don't attempt that.

---

### Post by mastablasta on 2020-10-30
> **jcdenton1995 said:**
> I'm actually looking at buying a graphics card right now so I'm also interested in this. I was leaning towards a AMD RX5700 XT basically because it's in my price range 

new models are around the corner so maybe they will drop price on the older ones. it is a good choice i think. 

i don't think i can handle so much power usage so i went with GTX1650 and HD monitor. circuit breaker muightnot handle it. we have 4 PC in that room and a large TV.
 i still don't really see the difference beyond HD unless i look very very close. on TV (which is HD) i can't see the difference between HD programs and normal ones. unless the normal ones are stretched (e.g. some old series). so i though i will save some money and just go with HD setup.

---

