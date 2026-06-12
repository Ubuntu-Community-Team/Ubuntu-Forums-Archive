---
title: "530n Memory Upgrade (and other questions)"
date: 2008-01-05
forum: Dell  Ubuntu Support
---

### Post by xptweakerntn on 2008-01-05
I JUST ordered the 530n from dell.
I got the

	Dell Inspiron 530:
Intel®Pentium® dual-core processor E2160 (1MB L2,1.80GHz,800 FSB)	 	SM216NH	 	[222-9346]	 	1
	Operating System:
Ubuntu Linux version 7.10 with DVD Playback	 	LINUXDV	 	[420-7917]	 	11
	Monitor:
No Monitor	 	N	 	[320-3000]	 	5
	Memory:
1GB Dual Channel DDR2 SDRAM at 667MHz- 2DIMMs	 	1GB62	 	[311-7237]	 	3
	Hard Drives:
250GB Serial ATA Hard Drive (7200RPM) w/DataBurst Cache™	 	250S	 	[341-4809]	 	8
	Optical Drive:
48X CD-RW/ DVD Combo Drive	 	L48COMB	 	[313-5269]	 	16
	Video Cards:
256MB NVIDIA GeForce 8600GT-DDR3	 	NV8600	 	[320-5747]	 	6
	Sound Cards:
Integrated 7.1 Channel Audio	 	IS	 	[313-2758]	 	17
	Keyboard and Mouse Bundles:
Dell USB Keyboard and Dell Optical USB Mouse	 	EKOM	 	[310-7966][310-8025]	 	

--------------
My questions are, as I am going to manually upgrade the memory, what does it come with? 5300 or 6400?
[http://crucial.com/store/listparts.aspx?model=Inspiron%20530](http://crucial.com/store/listparts.aspx?model=Inspiron%20530)
If it will support the 6400, I'll pay 10 more bucks. If not, the 530 hundred will be fine. I'll buy the 2x1gb, I'll end up with 3 gb. 

Also, what does the pc come with? Are the keyboard and mice anything special, or just the cheapest thing dell can find? I've got a nice set already, but it's getting old. 

Also, does the motherboard include any ide slots? As I'd like to use my drives (2 hard drives, and 2 optical drives) as well. I've read that it has extra spaces for 3.5" drives (hard drives), but does the motherboard have an ide controller? 
(if not, will one of the pci ide controllers that cost around $20 work well in ubuntu?). 

thanks, i'm looking forward to recieving it! i love linux, but my current system is a few years old, so I figured I'd support the cause!
:guitar::guitar::guitar::guitar:

---

### Post by gbrainin on 2008-01-05
I don't honestly know whether the memory is 5300 or 6400, but:

The keyboard and mouse are fairly standard.  Not the cheapest in the world, but nothing special, either.  You can substitute any USB keyboard and mouse.

There are no IDE slots on the motherboard, only SATA.  You can try a SATA to IDE adapter, but there are only 4 SATA controllers, total.  Otherwise, you're looking at some sort of PCI card.  I'd check the linux hardware compatibility list before buying: [https://wiki.ubuntu.com/HardwareSupport]("https://wiki.ubuntu.com/HardwareSupport")

---

### Post by xptweakerntn on 2008-01-06
Alright, that sounds good. I'll have to try the pci to ide thing, or perhaps a sata to ide adapter. I have a lightscribe drive i want to use, as well as 2 ide hard disks. So do you own a 530? If so, are your specs close to mine? Are you satisfied with the performance overall?

---

### Post by xptweakerntn on 2008-01-06
Oh, and unless i am missing something BIG here, it appears that my 8600gt isn't even compatible:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)
:)
I'm guessing that the list isn't updated as much as it should be?
:lolflag::lolflag::lolflag::lolflag:

---

### Post by gbrainin on 2008-01-06
Yes, I have a 530n, and it's fairly similar to yours--I have a core 2 duo processor and an older video card.  I am more than satisfied with its performance, but then again it replaced a system that was nearly 10 years old, so pretty much anything would impress me.

I believe the hardware list only gets updated when someone like you gets a new piece of hardware, sees how it works, and reports back.  So yes, there's some delay.  However, I also think that the 530n is now shipping with the proprietary driver enabled by default, so presumably Dell's checked the compatibility.

I notice that you did not purchase a monitor.  You may need to do some tweaking to make sure the settings are correct for your monitor.  (Of course, I got a Dell monitor, and I still had to do that.)

---

### Post by MJN on 2008-01-06
> **xptweakerntn said:**
> My questions are, as I am going to manually upgrade the memory, what does it come with? 5300 or 6400?
[http://crucial.com/store/listparts.aspx?model=Inspiron%20530]("http://crucial.com/store/listparts.aspx?model=Inspiron%20530")
If it will support the 6400, I'll pay 10 more bucks. If not, the 530 hundred will be fine. I'll buy the 2x1gb, I'll end up with 3 gb.

Your system comes with 667MHz DDR2 memory hence it will be using PC2-5300 modules (the 5300 is a measure of max throughput, 5333MB/s, that 667MHz DDR2 can provide).

Given you have an FSB of 800MHz, you would be able to 'take advantage' (it'd be difficult to directly observe the benefits other than on paper and/or a memory test) of 800MHz DDR2 memory i.e. PC2-6400. To put it another way, your system supports DDR2-667/PC2-5300 and DDR2-800/PC2-6400 memory.

**However**, you can't mix and match memory like this - or at least if you were to add a pair of PC2-6400 modules they would operate at the 'slower' PC2-5300 speed given your other modules. The memory bus does not run at the full FSB speed but rather a ratio of it and hence given this ratio has to be fixed, and all buses use the same ratio, it must run at a speed appropriate for the lowest common denominator.

Hence, I'd suggest just going with the PC2-5300 modules unless you're planning on upgrading the existing modules just round the corner.

Mathew

---

### Post by xptweakerntn on 2008-01-06
Alright..so This is what I am planning on: Getting 4x1GB sticks of the 6400. My brother's computer will support the ram included in mine, I believe. This is his ram:
[http://crucial.com/store/listparts.aspx?model=Pavilion%20a1310n%20Series](http://crucial.com/store/listparts.aspx?model=Pavilion%20a1310n%20Series)
Even though the ram included in my computer that i ordered is MUCH fast than his, if i put my excess ram in his computer, it'll run at the same speed as his ram, correct? that'll leave him with 1.5GB, and I'll have 4gb. Will this work as easily as planned?

Also, about the moniter: I am running ubuntu right now with the moniter, so it works, so I don't need any concern there, do i? 

Also, back to the memory. When purchasing memory, is that what you go by, the front side bus speed? Since mine is 800mhz, it will make the 6400 ram run at 800mhz? if i had a front side bus of 667mhz, i could only use the 5300? and if i had a front side bus of 667mhz, i COULD buy the faster ram, but it would "be backwards compatible" and run at a slower speed? I KNOW that that was confusing, but perhaps someone will understand. Thanks!

---

### Post by xptweakerntn on 2008-01-06
Correction, I knew something looked wrong:
my brother's computer is actually this:
[http://crucial.com/store/listparts.aspx?model=Pavilion%20a1310n%20Series](http://crucial.com/store/listparts.aspx?model=Pavilion%20a1310n%20Series)
I KNEW he had ddr2 memory!

---

### Post by MJN on 2008-01-07
Those links look the same to me but, assuming it was an error and your brother's PC does take DDR2 RAM then yes - your 'old' modules will work in his machine. This is the theory at least - some motherboard/memory combinations just don't get on. Dell's used to be a classic example of this and would sometimes reject memory that ought to work but general compatibility is probably a little better these days.
 
The issue of speeds is complex to say the least. The Front Side Bus essentially connects the CPU to the memory and hence its speed dictates the speed at which each of these operate at. In the case of your Core 2 Duo CPU the FSB actually runs at a clock speed of 200MHz but is 'quad pumped' to effectively run at 800MHz - this is achieved by the CPU acting on both the rising and falling edges of the waveform in addition to using two signals 90 degrees out of phase with each other (the latter gives two channels which is why you really need pairs of modules to take advantage of it). Mind-boggling, yes, but suffice to say the effective bus speed is a multiplier of the actual clock speed.
 
Now, this same clock speed is used to drive the memory chips and again 'pumping' is used to increase the effective speed. DDR and DDR2 are dual-pumped (this is the 'Double' bit in Double Data Rate) and I/O bus of the module is again clocked at twice the rate (the '2' bit) hence giving this effective '800MHz' transfer rate as per the CPU. DDR2-800 (PC2-6400) can take full advantage of this and provide the optimum transfer to/from the CPU.
 
That's probably raised more questions than it answer, but hopefully it illsutrates that there is more to 'matching' CPU/memory than the FSB speed given the concept of the lower underlying clock speed and the use of multipliers to increase this to the effective rates. It just so happens that in your case the CPU and memory are both employing similiar technologies such that they can both get 800MHz 'performance' out of a 200MHz clock.
 
If you did have a 667MHz FSB, common with the Celeron range, then you would not be able to take advantage of DDR2-800 memory - although it would work given it being backwards compatibile.
 
Whether you'll see any benefit of 4GB over 3GB is debatable, but if going down this avenue gets your brother an extra 1GB then I'm sure he wouldn't be too happy if I dissuade you! ;)
 
Mathew
 
P.S. Forgot about your monitor question - it should work fine, just requiring you to set the correct resolution to match your monitors native resolution (assuming it's an LCD). Don't worry about it though - most, if not all, monitors will tell you if your not running at the optimum resolution (and it'll look bad too) so you'll just have to play with the graphics driver settings.

---

### Post by xptweakerntn on 2008-01-07
Yeah, I figured I'd go with the 4GB, but I've seen varous tutorials saying that Linux doesn't even use it UNLESS you do something...however I don't remember what it was. Supposedly, anything over 1GB is just sorta ignored, but there is some sommand that will let you use it. Anyone heard of this?

---

### Post by MJN on 2008-01-07
If anything you'd probably find it's the other way round - i.e. the way Linux manages its memory is that more than you'd expect always appears to be in use. Many people find when, say, add an extra GB that their 'free' memory doesn't increase (and certainly not by a GB) - this is due to the way the kernel uses memory but doesn't waste time clearing it out until it's needed again (particularly if it ends up being the same process that wants to reuse it). This is particularly true when it comes to the disk cache - if something's being written to disk then there's a good chance it may need to be read back from it hence keeping the cache unflushed can pay dividends.
 
Mathew

---

### Post by xptweakerntn on 2008-01-07
Alright, sounds good. Now, once again, does anyone have any experience with either pci to ide cards or sata to ide converters?

---

### Post by xptweakerntn on 2008-01-08
Alright..so for all that's bought a delbuntu before...it is estimated that mine will be shipped the 16th, is that fairly accurate?

---

### Post by gbrainin on 2008-01-08
All I recall is that mine arrived significantly earlier than originally estimated.

---

### Post by xptweakerntn on 2008-01-08
I sure hope so, the estimation seems to be pretty long. I believe  my memory will arrive sometime about a week from today...depending when it ships. I ordered the faster memory, 4 1GB sticks.I'm just wondering...it's somewhat cold here, and will be probably around 15 Fahrenheit when it arrives here (the memory), I know sticks of memory are meant to take high temperatures, but can low temperatures hurt anything? Theoretically, if they are really cold, and then you put them in a machine and use them right away, couldn't that damage them? As I'll have my memory a few days before my system, it'll have time to join room temperature, but I'm just wondering if that could be a concern for someone.

---

### Post by xptweakerntn on 2008-01-08
Whoa! I just checked the dell site, my purchase shipped today! I ordered it the 5th, it shipped the 8th! So I assume it'll be here by Saturday, that's great! I may get it before my memory!

---

### Post by xptweakerntn on 2008-01-09
Ok..got the system and the ram today...installed ram..it works. However...only 3.2Gb of 4 is showing up the system moniter...just like in this post:
[http://ubuntuforums.org/showthread.php?t=546943](http://ubuntuforums.org/showthread.php?t=546943)
any ideas? will the 64bit version solve this?

---

### Post by Trindol on 2008-03-26
> **xptweakerntn said:**
> Ok..got the system and the ram today...installed ram..it works. However...only 3.2Gb of 4 is showing up the system moniter...just like in this post:
[http://ubuntuforums.org/showthread.php?t=546943](http://ubuntuforums.org/showthread.php?t=546943)
any ideas? will the 64bit version solve this?

If you are running 32 bit Ubuntu, then you will only be able to see 3.2 GB of ram regardless of how much is installed. That's for any 32bit OS. If you upgrade to 64 bit Ubuntu you will be able to see all 4GB. HOWEVER: the Dell 530N comes with a bios that is very limited. You must flash your bios to version 1.0.12 which was just released on Mar. 17. The previous versions of the BIOS will not allow you to see over 3.2 GB RAM despite the fact that the rest of the hardware is 64bit.

---

### Post by tgrimley on 2008-05-30
> **Trindol said:**
> If you are running 32 bit Ubuntu, then you will only be able to see 3.2 GB of ram regardless of how much is installed. That's for any 32bit OS. If you upgrade to 64 bit Ubuntu you will be able to see all 4GB. HOWEVER: the Dell 530N comes with a bios that is very limited. You must flash your bios to version 1.0.12 which was just released on Mar. 17. The previous versions of the BIOS will not allow you to see over 3.2 GB RAM despite the fact that the rest of the hardware is 64bit.


weird...

```
tgrimley@gutsy:~$ uname -a && free -m
Linux gutsy.mit.edu 2.6.22-14-server #1 SMP Tue Feb 12 08:27:05 UTC 2008 i686 GNU/Linux
             total       used       free     shared    buffers     cached
Mem:          4050       3851        199          0        108       3302
-/+ buffers/cache:        440       3610
Swap:         2055          0       2054
```

---

