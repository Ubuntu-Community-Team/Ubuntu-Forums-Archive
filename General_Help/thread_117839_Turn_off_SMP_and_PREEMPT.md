---
title: "Turn off SMP and PREEMPT?"
date: 2006-01-15
forum: General Help
---

### Post by kg6gfq on 2006-01-15
Could someone please explain how to turn off SMP and PREEMPT?  Apparently they can cause problems with the RT2500 wireless drivers, which I would like to have working.  

Are they even on by default?  I ran across one thread that made it sound that way, but without clear instructions for turning them on/off.  

Thanks in advance!

---

### Post by mgor on 2006-01-15
you'd have to recompile your kernel,
[http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835)

and on step 4), make menuconfig, look for the options and disable them. can't pointout exactly where they are since i don't have any kernel source to run menuconfig on.

---

### Post by dcstar on 2006-01-15
[QUOTE=kg6gfq]Could someone please explain how to turn off SMP and PREEMPT?  Apparently they can cause problems with the RT2500 wireless drivers, which I would like to have working.  

Are they even on by default?  I ran across one thread that made it sound that way, but without clear instructions for turning them on/off.  

Thanks in advance![/QUOTE]
If you are using a SMP kernel, simply install and use the non-SMP version for you processor (via Synaptic).

---

### Post by newuser111 on 2006-01-16
ubuntu kernel doesnt use preempt as far as I know (i could be wrong)

just install the generic 386 or 686 kernel, only the SMP kernel has SMP activated

---

### Post by kg6gfq on 2006-01-16
Well, I recompiled and made sure SMP and PREEMPT were off.  It still doesn't work, so I'm looking through other posts of similar problems to see if it could be anything else.  I gave more info on the problem at [http://ubuntuforums.org/showthread.php?t=117511](http://ubuntuforums.org/showthread.php?t=117511) if anyone knows what to make of that.  I've also asked about it over at the serialmonkey forums, devoted to RT2x00 chipsets.  Maybe they'll be able to help.  Thanks everyone for the instructions and advice!  (By the way, I'm pretty sure you're right about SMP and PREEMPT not being enabled by default.)

---

### Post by newuser111 on 2006-01-16
why don't you use ndiswrapper and install the rt2500 windows drivers?

---

