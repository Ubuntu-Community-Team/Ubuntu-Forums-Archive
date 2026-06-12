---
title: "Did hot Gutsy ruin my m1330 GPU?"
date: 2008-03-20
forum: Dell  Ubuntu Support
---

### Post by Zeedok on 2008-03-20
I just had the motherboard of my 3 month old dell xps m1330 (2.4GHz d/c, 4GB RAM, NVidia GeoForce 8400) replaced today.

Over the last week I noticed flickering and freezing of the screen (initially in Vista, then in Gutsy Ubuntu as well).  Eventually it just stopped booting at all.  Dell were OK about it and all I lost was two days of having a laptop.

What I am worried about is this happening again.  From some reading (and talking to the tech) it seems GPUs fail when laptops overheat - and high spec, small systems like mine are likely to overheat after long periods of time.  I use this thing for hours and hours every day!!

I have ordered a cooling laptop platform and installed temp monitors in Ubuntu and Vista and one thing I have noticed (like others have mentioned) is the different temp that Ubuntu runs compared to Vista (eg high 20'sC for Vista, low 40'sC for Ubuntu).  While I appreciate that they 'are rated to 80-90C', I just had the motherboard replaced so I am anxious about any high temp reading.

I know there are packages to control fanspeed and CPU scaling, but I wonder whether Dell itself has considered making such a tool easy to install, use and configure (I'm not sure that the current offerings are any of these!).  I mean, it must cost the company heaps to replace a motherboard, so they have a vested interest (as do I).

Can anyone offer some words of advice - or at least reassure me that Dell maybe are looking into this? Also, why is Vista (an inferior OS in my opinion) running cooler than Ubuntu? Is it a calibration issue (ie a false temp)?  What else can I do to protect my laptop?

---

### Post by oskar-swe on 2008-03-20
I have a very similar laptop and I'm interested in monitoring temperatures for various stuff. What monitors are you using? What temp intervals are considered ok/normal, for cpu/gpu etc?

---

### Post by sdennie on 2008-03-20
On an XPS m1330, the primary fans are located in the back left side of the machine.  If you are using a 4 or 6 cell battery, it sits flush with the laptop and limits airflow.  The 9 cell battery actually lifts up the machine and regardless of whether or not it's on a desk or your lap, gets much better airflow.  

I've only had my m1330 for a few weeks (configured almost identical to yours) but, in general, the CPU idles around 35C and the GPU idles at around 56C.  Those numbers can vary greatly (even with the lift of the 9 cell battery it's possible to obstruct the fans) but, even under very heavy load and me being lazy and obstructing the fans, it still is FAR under any kind of panic level.

I would either buy the 9 cell battery or be mindful of where the vents are under the machine and avoid obstructing them.  

The Vista temps you were seeing seem false to me.  It's entirely possible to get the CPU to sub 30C temperatures but, it would require aggressive power savings to do so.  I just pulled the power cord off my XPS m1330 and powertop claims that I'm using slightly less than 14W (so, more than 7 hours of battery), and even after a few minutes my CPU only dropped down to 33C.

---

### Post by Zeedok on 2008-03-20
@oskar-swe - I can't quite remember what the steps for installing the sensors were, but I found the instructions here on Ubuntu forums (the app is called gnome sensors-applet).

@vor - the vista temps may well be incorrect.  I am using speedfan, I don't know how reliable it is.  I know that the GPU is supposed to handle >80C +, but if temps weren't what ruined my GPU then what else was it? Could have been a faulty card I guess.  I just want to take all the precautions I can.

I'll be really disappointed if this laptop turns out be a dud and fails frequently (even though it is under warranty!)

PS It was eye popping the way this guy pulled apart my laptop, replaced the motherboard and put it all together again inside 20mins!

Any further advice gratefully received.

---

### Post by adult swim on 2008-03-20
ive got a dell box and use gkrellm and the i8k plugin to control my fans.  you can set a temperature, i use 40C plugged in and 45C on battery, and whenever you computer gets to that temperature the fans will kick on automatically and turn off when the temperature goes down below the level you set. if you are interested the 12th post in this link has a walkthrough [http://ubuntuforums.org/archive/index.php/t-472567.html](http://ubuntuforums.org/archive/index.php/t-472567.html)

---

### Post by sdennie on 2008-03-20
> **Zeedok said:**
> 
I'll be really disappointed if this laptop turns out be a dud and fails frequently (even though it is under warranty!)

PS It was eye popping the way this guy pulled apart my laptop, replaced the motherboard and put it all together again inside 20mins!

Any further advice gratefully received.

It's entirely possible that you simply had some faulty hardware to begin with.  As far as I've seen, there is nothing inherent in Ubuntu that would kill an m1330.  Depending on what hard drive you have, the lax Ubuntu default power savings might slowly do damage to your disk but, after 3 months, it would have been impossible to do any real damage (Google Load_Cycle_Count for more information on this problem).

As I said, I've only had an m1330 for a few week but, it really is running like a champ.  It runs cool, the battery life is great and I've not seen any problem that looks hardware related.  It really may have been a one off hardware problem that you experienced.

---

### Post by laradji on 2008-03-20
Its seem related with this post :

[http://ubuntuforums.org/showthread.php?t=697925](http://ubuntuforums.org/showthread.php?t=697925)

I think we perhaps make one post for all this problem with nvidia card and dell laptop.

---

### Post by DrMega on 2008-03-20
You said that Vista reported the temperature to be in the upper 20s. This doesn't seem right to me, as normal room temperature is generally considered to be mid twenties.

You said the problem started in Vista, and then started in Ubuntu as well. With this point, and the suspiciously low temperature reported by Vista, I'm wondering if Vista failed to monitor the temperature correctly and failed to turn on the fans when things started getting a bit too warm.

---

### Post by IsawSp4rks on 2008-03-20
While I'm no fan of Vista and I do prefer to use Ubuntu, I do think that Vista (XP too) would have much better power management facilities and better driver support than Ubuntu (or any GNU/Linux distro for that matter) purely because MS are more closely aligned with hardware developers.  IHVs see Linux Desktop support as an aside for the most part though this is changing with various hardware vendors coming onboard.

I also notice my GPU is hotter in Ubuntu when using a laptop.  I think that power management of GPU functions needs to be prioritised in Hardy and further releases.

---

### Post by tgalati4 on 2008-03-20
A few years ago, Intel and others went to a Ball Grid Array manufacturing for surface mount chips.  This eliminated the traditional gold pins and sockets or side legs for chipsets.  This was an obvious cost savings.  The replacement attachment is now using ~1200 small balls of solder to attach a chip to the motherboard.

When a chip heats up, the thermal stresses can cause the chip to curl putting stress on these small balls of solder.  After so many thermal cycles, small cracks develop in the solder causing "cold junctions".  This can result in intermittent behavior.

The temperatures at which this occur is much lower than the die maximum temperature (~70C to 90C) that most thermal alarms are set to.  Using your laptop as a desktop machine with the CPU set to "High Performance" can accelerate this process.

Since your machine is new, you have provided Dell with an important data point.

---

### Post by sdennie on 2008-03-20
> **IsawSp4rks said:**
> While I'm no fan of Vista and I do prefer to use Ubuntu, I do think that Vista (XP too) would have much better power management facilities and better driver support than Ubuntu (or any GNU/Linux distro for that matter) purely because MS are more closely aligned with hardware developers.  IHVs see Linux Desktop support as an aside for the most part though this is changing with various hardware vendors coming onboard.

I also notice my GPU is hotter in Ubuntu when using a laptop.  I think that power management of GPU functions needs to be prioritised in Hardy and further releases.

I'm not sure that's true.  A good linux distribution will likely have drivers for more hardware than Vista and I can't even count the number of times I've had to bring an Ubuntu laptop to help a friend download the 20 million drivers that they need to get their XP laptop running after the ritual re-install every few months.  For any modern laptop, it's probably much easier to install Ubuntu than it is to install XP because the drivers are simply installed on the system to begin with.

As far as heat and power savings are concerned linux is actually MUCH better than XP/Vista.  The difference is that, unfortunately, in Ubuntu, there is no button to press that says, "Use less power when I'm on batteries."  The exaggerated marketing hype for my laptop claims that it can go up to 7 hours on batteries.  That's a completely unrealistic measure if you are doing anything remotely useful but, going to the same extremes that the marketing people are likely going to, under linux I could claim to get well over 8 hours of battery life (after a hell of a lot of tuning).

In reality, linux provides a much better platform for power savings than Windows does simply because of the nature of the platform.  Almost everything can be tuned at a very low level, interfaces can be added as needed, etc.  It would not surprise me one bit if Intel tested power saving features on linux before Windows simply because it's much easier to play around with the linux kernel than the Windows kernel.

I admit that I'm biased because I haven't used a Windows machine (outside of VMs) in many years but, in True Linux Fashion, linux isn't worse, it's just harder.  Once you get it running well, in nearly every respect, it makes software from MS look like what it is: Junk.

---

### Post by Zeedok on 2008-03-21
I was just watching some video on Vista (window DRM arrrgh!!).

The CPU temps were more like low thirties for most of the time, though by elevating the laptop to allow the heat to escape I kept it under control.  I guess taking precautions when using it for long periods is the best I can do.  I do wonder though, whether the default control of the fan in Ubuntu needs adjustment - ie I think it comes on sooner in Vista than in Ubuntu - maybe I'll try to install those packages and reset my own fan.  

I still reckon this would be a great target for Dell to fix up their linux support.

Thanks for all the comments - I'll let you know if I burn out any more GPUs!!

---

### Post by dasunst3r on 2008-03-21
My Inspiron E1505 with the nVidia graphics card option runs at 49 C to 57 C.  It's still working great. :)

---

### Post by Zatarhi on 2008-03-21
I agree about the false readings theory - a discrete video adapter in a well cooled tower usually doesn't idle below 35 degrees or so - in a laptop it will run hotter.

In addition, temperature monitors in Windows aren't always correct - I've seen the BIOS will report one temperature, and a monitoring utility will report another (usually lower than the BIOS)...and yet another monitoring utility will report yet another temp...

I've got an Athlon (passively cooled) and a GeForce 7600GS (again, passively cooled) in my tower - they both run significantly cooler under Ubuntu when not under full load.

Just my .02 - YMMV.

---

### Post by Zeedok on 2008-03-22
I have successfully installed gkrellm following the instructions that adult swim pointed me towards.

A couple of observations . . .

1. I have noticed that the cpu usage (and consequently the temperature) charges up when I look at any flash video on the web (eg YouTube)
2.  I just had a long browse with firefox and noticed the temp soaring.  The cpu was running at 40% (all from Firefox) and the temp was up at 68-70 degrees.  By closing and restarting firefox I got the cpu usage back down to 2-5% and the temp to 39 degrees.

I am presuming that this is the 'memory leak' or whatever it is called that Mozilla is trying to get rid of in firefox 3.  Correct?

---

### Post by sdennie on 2008-03-22
> **Zeedok said:**
> I was just watching some video on Vista (window DRM arrrgh!!).

The CPU temps were more like low thirties for most of the time, though by elevating the laptop to allow the heat to escape I kept it under control.  I guess taking precautions when using it for long periods is the best I can do.  I do wonder though, whether the default control of the fan in Ubuntu needs adjustment - ie I think it comes on sooner in Vista than in Ubuntu - maybe I'll try to install those packages and reset my own fan.  

I still reckon this would be a great target for Dell to fix up their linux support.

Thanks for all the comments - I'll let you know if I burn out any more GPUs!!

What type of video?  Something like xvid or even DVD should be largely offloaded to the GPU (which won't struggle under it) but, watching flash videos (or flash in general) in a web browser is probably the most CPU/GPU intensive task that a non-gamer or developer is every likely to do.  Displaying a tiny youtube sized video in a web browser on linux will essentially put a CPU (or core) close to max power.  That's not really a limitation of linux but of the adobe flash player.  I don't know if abobe flash is more efficient on Windows but, on linux, it will drain battery life or heat up a CPU faster than almost anything.

---

### Post by Zeedok on 2008-03-22
What you're saying makes sense.  I'm sure most people happily watch youtube etc without giving 'heat' a second thought.

Flash really does boost the cpu/temp.  Guess it doesn't really matter unless you watch heaps of flash.

---

### Post by sdennie on 2008-03-22
> **Zeedok said:**
> I have successfully installed gkrellm following the instructions that adult swim pointed me towards.

A couple of observations . . .

1. I have noticed that the cpu usage (and consequently the temperature) charges up when I look at any flash video on the web (eg YouTube)
2.  I just had a long browse with firefox and noticed the temp soaring.  The cpu was running at 40% (all from Firefox) and the temp was up at 68-70 degrees.  By closing and restarting firefox I got the cpu usage back down to 2-5% and the temp to 39 degrees.

I am presuming that this is the 'memory leak' or whatever it is called that Mozilla is trying to get rid of in firefox 3.  Correct?

Looks like we came to the same conclusion about 5 minutes apart.  I'm not sure that anything can be done about flash eating an entire core while watching a video.  You could try to use gnash instead of the adobe player but, I don't know how well it works these days or if it will be lighter on the CPU.  The problem really is with adobe and not something inherit in linux (watching Hi-DEF non-flash video on my machine leaves my CPU nearly idle).

I watched a football match via flash today on batteries.  When writing code, I can get 6+ hours of battery life on this machine.  While watching a football match via flash, I had to turn down the monitor brightness and suspend the machine during half time just to make sure I had enough battery life to finish the match...

---

