---
title: "STR suspend to ram Asus PTGV-DM   HP Onyx2"
date: 2010-04-28
forum: Desktop Environments
---

### Post by harrismh777 on 2010-04-28
Greetings folks,
Thought I would start here;  I am running Jaunty 9.04 with updates (works well, thanks) and have a small issue with STR suspend to ram waking up.
The machine is an HP s7400n slimline, using the Asus PTGV-DM , HP Onyx2, motherboard with a *very* slimmed down BIOS interface (no options for STR for instance, and *nothing* about power management.

Hibernation works fine, and wakes fine;  however, suspend to ram, STR, refuses to wake under any conditions. It does suspend, the blue power light turns yellow, and the machine "looks, and feels" suspended; however, network traffic to the machine does not wake it... also, manually pressing the power key does not wake it either. 

The power key "looks" like its waking (the power light goes blue, the hard disk light blinks) but the machine does not wake and the whole thing has to be powered down hard and restarted. 

Any ideas on how I might diagnose this, debug this, and get some clues as to what is happening here?  My web searching isn't turning up much. 
:confused:

PS:  as an aside, does anyone know if the BIOS on this specialty board can be flashed?  I am willing to approach this from either a HW or SW side.  Thanks.

Thanks in advance.

regards,

---

### Post by DrWig on 2010-04-28
I'm having similar problems with my old ACER.  Just found this post, and will try out the solution tomorrow....might help you too:

[http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html](http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html) 

cheers

DrWig

---

### Post by harrismh777 on 2010-04-28
> **DrWig said:**
> I'm having similar problems with my old ACER.  Just found this post, and will try out the solution tomorrow....might help you too:

[http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html](http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html) 

cheers

DrWig

Thank you. This is interesting, because it tends to imply that the problem is NOT the motherboard... or the BIOS. If its in the HAL scripts, what in the world is taking so long getting this thing fixed?  I am noticing that suspend|hibernate is a crap shoot in ubuntu... but depending on the machine the symptoms vary widely!  That surprises me.
:-k

---

### Post by harrismh777 on 2010-04-28
Ok, I dug into this a bit... now that I know where to look... and found in this directory:
   /usr/lib/hal/scripts/linux
a file called:
   hal-system-power-suspend-linux

This file details a series of quirks for getting the video resume to work. So, I am wondering whether the video hardware is the real problem in all of this suspend|hibernate mess with ubuntu. It is looking to me like the various symptoms are caused based on the installed video hardware, and what it takes to resume the video.
This begs the question, how do we determine what video quirks our system has in order to get the hal scripts fixed for our installations?
So, if this is the real issue, who should get the attention for getting this fixed... or better, is there a place to "read" to get some background into this thing for diags and self-help?  
Very frustrating.
#-o

---

### Post by DrWig on 2010-04-29
I'm going to try a few things this morning too.  I also think that, at least for my suspend issue, it's gfx related so thanks for the heads up on that file....

Suspend/hibernate issues seem to be massive in Ubuntu, and I think need looking into with elevated priority.

cheers

DrWig

---

### Post by DrWig on 2010-04-29
Just looked at the file you mentioned

> This begs the question, how do we determine what video quirks our system has in order to get the hal scripts fixed for our installations?

Blooming good question!  Anyone?

---

### Post by DrWig on 2010-04-29
s2ram (needs installing first, I think) states:

[http://en.opensuse.org/S2ram#Troubleshooting](http://en.opensuse.org/S2ram#Troubleshooting)

Allowing me to try the different workarounds (s2ram doesn't support my hardware, so I need to try them all out)....here goes....

---

### Post by DrWig on 2010-04-29
Nothing worked work.  Found this stress test:
[https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting)

My laptop fails the first two tests and can't continue (have to hard reset).

It's supposed to generate a bug report automatically, but it isn't.....I'm going to try and trick it into doing so now (I've no idea how to put in a bug report otherwise....)

cheers

DrWig

---

