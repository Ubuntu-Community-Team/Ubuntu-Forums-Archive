---
title: "XPS m1330 freezes after upgrading to 8.10"
date: 2008-11-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jepser on 2008-11-03
I updated my Dell XPS m1330 from 8.04 to 8.10 yesterday via the update manager. It works well overall but I have a big problem, the computer freezes. When the freeze kicks in the caps-lock and the num-lock light starts to blink and I can't do anything else but push the shut-down-button. The freeze kan start whenever, without any warning.  It can freeze after 5 min or after I've been using the computer for 1½ h and it doesn't

mather if the computer is in use or if it's untouched. 

 

Have anyone experienced this problem or know how to fix it?

---

### Post by treris on 2008-11-04
There is supposedly a bug in the intel wireless card driver for the 4965AGN cards. Have you tried updating your system installing the instructions below?

> System lock-ups with Intel 4965 wireless

The version of the iwlagn wireless driver for Intel 4965 wireless chipsets included in Linux kernel version 2.6.27 causes kernel panics when used with 802.11n or 802.11g networks. Users affected by this issue can install the linux-backports-modules-intrepid package, to install a newer version of this driver that corrects the bug. (Because the known fix requires a new version of the driver, it is not expected to be possible to include this fix in the main kernel package.) 

I have a xps m1330 as well and I can't say that I've freezes like the ones your describing.

---

### Post by Jepser on 2008-11-04
Thanks for the tip! I have now tried it and will reply when i can evaluate it : )

---

### Post by treris on 2008-11-04
Good luck, hope it helps. 
By the way, welcome to the ubuntuforums!

---

### Post by Zeedok on 2008-11-05
I hope that is your only issue.

I recently upgraded to Intrepid on my m1330 and shortly after my computer was freezing frequently.  I dual boot with vista, so I booted into vista and it continued even on windows.  Unfortunately, I have had similar problems on my m1330 before, with intermittent freezing, coloured stripes on the screen etc.  On that occasion, I had to have my motherboard replaced.  I am awaiting a new motherboard.

This is, unfortunately, a well recognized problem with the m1300 and a bunch of other laptops, both from Dell and other manufacturers.  The problem apparently stems from a fault with the graphics card.   [Here]("http://direct2dell.com/one2one/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx") is a post on the Direct to Dell blog with more information.

Like I said, I hope your issue is just software . . .

---

### Post by treris on 2008-11-05
> **Zeedok said:**
> 
This is, unfortunately, a well recognized problem with the m1300 and a bunch of other laptops, both from Dell and other manufacturers.  The problem apparently stems from a fault with the graphics card.   [Here]("http://direct2dell.com/one2one/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx") is a post on the Direct to Dell blog with more information.

Aha, that nVidia problem again. I, fortunately, don't have that problem because I chose for the intel x3100 card since I didn't need more graphic power and needed the powersaving more. In hindsight that was a lucky call.

Let's indeed hope that that is not what is causing problems for Jepser.

---

### Post by Zeedok on 2008-11-05
Apparently my new motherboard is from a 'new batch' and will prevent the issue from happening again.

Third time lucky I hope.

I was fantasizing that maybe Dell would throw in a mini 9 inspiron for the inconvenience . . .

---

### Post by treris on 2008-11-06
> **Zeedok said:**
> Apparently my new motherboard is from a 'new batch' and will prevent the issue from happening again.

Third time lucky I hope.

I was fantasizing that maybe Dell would throw in a mini 9 inspiron for the inconvenience . . .

That would be nice, wouldn't it, I've heard that they are fanless so that means that they are completely quiet if you're using an ssd, niceness!!

But then again, my xps 1330 isn't noisy either and is still quite portable and everyting, so for now I'll stick with it. haha

Wasn't there some sort of bios update as well for the xps laptops with nvidia graphics? One that would let your fans turn more to keep your gpu cooler?

---

### Post by Zeedok on 2008-11-06
Well now using my m1330 with it's third (correct third!!) motherboard.  I have installed the latest version of the bios (A12) and I am anxiously watching the GPU temp.

Hopefully all will be well . . .

---

### Post by Jepser on 2008-11-07
I can now tell that the fix for my freezing-problem worked! It haven't freezed since. Thanks alot!

---

### Post by treris on 2008-11-10
I hope it still hasn't frozen up on you, enjoy your 1330!

---

### Post by jacrider on 2009-01-04
> **treris said:**
> There is supposedly a bug in the intel wireless card driver for the 4965AGN cards. Have you tried updating your system installing the instructions below?



I have a xps m1330 as well and I can't say that I've freezes like the ones your describing.


We have the Intel 3945 card in our M1330.  Any ideas about how to install the drivers available from Intel.  I can't seem to figure out how to do it, but we are experiencing the same lock-up issues with the flashing scroll-lock and num-lock indicators.

Thanks.

---

