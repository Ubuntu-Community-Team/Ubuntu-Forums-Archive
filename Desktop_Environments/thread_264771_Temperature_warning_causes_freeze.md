---
title: "Temperature warning causes freeze"
date: 2006-09-25
forum: Desktop Environments
---

### Post by dizm on 2006-09-25
I've been having sporadic random (total) freezes.

I've traced them to a thermal warning at 70C.  If I disable the warning (a BIOS CMOS setting) I don't freeze, even if I spike above 70C.  Since I'm usually around 60C, I'd like to turn this into a more polite warning.  

I can't find any info on what the setting does, and what happens to the warning that causes the freeze.

Any ideas?  

Running more or less up-to-date Dapper
Kernel: 2.6.15-26-686
CPU: Intel P4 3.00 GHz
Chipset: Intel 865PE
Mobo: DFI 865PE-ALE

---

### Post by lagagnon on 2006-09-25
This has absolutely nothing to do with Ubuntu and everything to do with your hardware and your BIOS. I would suggest that even getting to 60C is dangerous and if you have your CPU at that temp for any extended period of time it will most certainly reduce its normal lifespan.

You should:

1) clear all dust out of your machine and especially on the fan blades and within the blades of the heat sinks, esp. the CPU heat sink.

2) renew the CPU heat sink to CPU die heat transfer compound.

3) check if you have a process that is hanging and consuming a lot of your CPU activity (run "top".)

4) think about upgrading or adding more fans to your system.

5) do not remove the thermal warning from your BIOS - you do so at your own risk.

I cannot help you with the BIOS settings - every motherboard's BIOS is different. You should read your motherboard manual and the info at your motherboard manufacturer's website and also at the website of the BIOS writer. Find out what BIOS you have and do some googling around.

Larry, A+ certified tech.

---

### Post by dizm on 2006-09-25
Thanks for your generous help and advice Larry.

I hate to go on the defense, but...
- Ubuntu produced the kernel which freezes
- The Ubuntu community knows heaps, and is v.helpful
- I've already done your steps 1-4 (step 5 is a workaround/diagnotic trick)
- I did heaps of googling before resorting to this post
- The BIOS writer is doing the MS thing - hiding behind a third party.  I cannot find ANY details on the BIOS
- The mobo maker is similar - I only have install docs

Having said all that, if a moderator says 'leave', I'll go (one of the rules is to not moderate one another :-).  Meanwhile:

The BIOS is Award v6.00PG (sorry, forgot that last time).

Any help with BIOS/mobo docs?  Any help with tracing the kernel freeze to the source?

---

### Post by lagagnon on 2006-09-25
I don't think it is the kernel which is freezing it is your hardware! If I were you, in order to once and for all determine if you have a hardware rather than software problem (and I'll bet you 9 to 1 it is) you can download the Overclockix Live Linux CD and run some of the stress test stuff on that CD. If your system freezes using the tests on that Live CD it is NOT Ubuntu but it is your computer.

[http://overclockix.octeams.com/](http://overclockix.octeams.com/)

---

### Post by WalmartSniperLX on 2006-09-25
LOL 70 degrees is DEADLY for ANTYHING except maybe a graphics card, which can handle well over 200 degrees F. 

Its not ubuntu or its kernel, its your hardware. 

If its your cpu, then thats really dangerous. You dont want your cpu reaching past 60 degrees C. And as I said you wouldnt 'like' it to, I mean that it isnt safe, but it is possible for some cpus to operate at such temps and hotter. 

Cpus that reach hot temps will hang the entire system. If its your mobo temps (chipset), the same issue will occur

But what is interesting is that if you disable the warning it doesnt hang. Either way I wouldnt blame ubuntu. If disabling something on your bios fixes the prob, then it isnt the os, but your chipset

Sorry if this doesnt help much :-?  but honestly I would make sure your temps are lower in general.

---

### Post by CaveRat on 2006-09-25
I would like to add my 2 cents here too. They are right. The OS does not cause the CPU to heat up like that. Not enough ventilation, built up dirt in the heatsink, a worn out Fan on the heatsink, too small or slow a fan on the heatsink, etc. Get some Arctic Silver 6 for the sink. Take the side off the case for awhile and see if the CPU cools down for now.

---

### Post by Anduu on 2006-09-26
Just to note...while 70 degrees C is high it is not exessive for some AMD processors.

During summer months when the ambient temp is 30+ my AMD Athlon XP2200+ idles between 60 and 65 degrees.According to a source which I cannot find at the moment(I'll try to track it down again...)my cpu reaches critical at 90+degrees!

From everything I have heard Intel cpus won't even get close to 70 degrees before locking up.Are you sure your temp readings are correct?

---

### Post by Anduu on 2006-09-26
Well I found that info...

[http://www.heatsink-guide.com/content.php?content=maxtemp.shtml](http://www.heatsink-guide.com/content.php?content=maxtemp.shtml)

According to their numbers your cpus max temp is 69.8 so yes you have a heat problem for sure.

I would replace your cpu fan and redo the thermal compund.Maybe even a new case fan.Also make sure your power supply fan is clean/working.

Even though disabling the alarm in the bios stops the freeze i doubt it would go much longer without freezing under load.

---

### Post by kerry_s on 2006-09-26
I would check if your motherboard/cpu is software controlled you might just need a driver. Mine is AMD so i use athcool, with out athcool my temp is 50-60, with athcool i run between 30-40.

---

### Post by WalmartSniperLX on 2006-09-26
> **Anduu said:**
> Just to note...while 70 degrees C is high it is not exessive for some AMD processors.

During summer months when the ambient temp is 30+ my AMD Athlon XP2200+ idles between 60 and 65 degrees.According to a source which I cannot find at the moment(I'll try to track it down again...)my cpu reaches critical at 90+degrees!

From everything I have heard Intel cpus won't even get close to 70 degrees before locking up.Are you sure your temp readings are correct?

ahh yes athlonXPs do run hot, but run fine. My friend has an XP, not sure what model. It beats my sempron sadly in some ways. His is a barton core lol.

EDIT: o yeah man and make sure you take care of that fast, because you never know when that cpu will fry, and it just wont boot anymore ](*,)  happened to me and a horrible server I was setting up lol

---

### Post by dizm on 2006-09-26
Ok guys, thanks for all the input, although some are missing the point (please read my original post).

The issue is NOT:
 - why is the CPU getting hot?, or
 - what to do about it?
although the idea of a cpu driver is worth looking into.

The issue IS: why is the kernel behaving badly when CPU hits max temp?

Here is more info from the cpu spec (intel doc '30056103.pdf'):

As someone said, the CPU max case temp is around 70C.
The CPU does NOT freeze or fry at this temp.  This is the max OPERATING temp.
The cpu is designed to operate indefinitely at this temp.

Above an internal temperature threshold (unspecified, but surely close to 70C),
the cpu asserts the PROCHOT# (processor hot) pin, fires off an interrupt,
and starts protecting itself by skipping some clock cycles.

I suspect that the kernel is not properly handling this interrupt, and THAT's what's causing the freeze.

At a second threshold, some 20C higher (around 90C), the cpu does freeze.
This is the temp above which the cpu would fry.

What about the bios?  Well, once we boot linux, bios is out of the loop.  
Linux (wisely) does not use any bios code.  
So why does the behaviour depend on the bios setting?
Here's what I think is happening:

Just like the cpu, the bios has two thresholds, a warning temp and a critical shutdown temp
(although I'm confused about how they can be configurable, since the cpu thresholds are not configurable).

The warning can be enabled/disabled.
If it's enabled, bios enables the PROCHOT interrupt, with a vector pointing into bios.  
But since the kernel does not replace this vector, when the interrupt fires, 
bios takes over the cpu and the system locks up.

If the warning is disabled, bios disables the PROCHOT interrupt.  Hence, no freeze.

If I'm correct, this is a kernel problem which we should pass upstream.  I will look for a kernel forum to take this to.

Cheers.

---

