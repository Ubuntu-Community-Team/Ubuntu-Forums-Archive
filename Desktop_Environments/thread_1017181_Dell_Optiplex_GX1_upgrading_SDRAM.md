---
title: "Dell Optiplex GX1 upgrading SDRAM"
date: 2008-12-20
forum: Desktop Environments
---

### Post by gusteman on 2008-12-20
Hello Community, first of all let me wish you all a Merry X-mass and a Happy 2009 :KS
Now here goes: I use a Dell Optiplex GX1 450Mhz Pentium III with 256Mb SDRAM.
For the time being there are 3 SDRAM bars installed: twice 64Mb and one 128Mb. I really would like to repace these bars by 3 bars of 256Mb but when I do so the bios setup tells me that I have no more memory at all. If I get it right this means that the bios does not recognise the RAM I inseted. Anyone has a solution? I checked out the DELL support sites but asides lots of help for problems with any Windows OS's it didn't get me any further. So it would be nice if one of you could help me out on this. I am running Gutsy and would like to upgrade to Hardy but with the memory I have for the time being my PC might be reduced to the sped of a snail, if you see what I mean!!
Greets from Gusteman :guitar:

---

### Post by arepaking on 2008-12-20
Hi!
First of all, let's check that the memory that you are installing complies with the system specs. You can do the comparison against this information for the Optiplex GX1:

Memory
**Architecture** 	64-bit (non-ECC) or 72-bit (ECC), noninterleaved
**Wait states **	near zero
**DIMM sockets** 	three (gold contacts)
**DIMM capacities** 	32-, 64-, and 128-MB non-ECC SDRAM ("PC100" 100 MHz);
32-, 64-, 128-, and 256-MB ECC SDRAM ("PC100" 100 MHz)
**Minimum RAM** 	32 MB
**Maximum RAM **	768 MB
**Memory access time** 	synchronized with system clock
**BIOS address** 	F0000h

More info about the specs:
[http://support.dell.com/support/edocs/systems/ban_gx1/specs.htm](http://support.dell.com/support/edocs/systems/ban_gx1/specs.htm)

Check also that your BIOS is up-to-date. I notice that for your computer there is a BIOS update.

---

### Post by SAE140 on 2009-01-25
Of all my vintage machines a GX1 is my favourite. 
With regard to memory, take Dell's spec with a pinch of salt - it's possible to install 3 x 256 sticks of non-ECC providing you have the right brand of memory. The only way of knowing for sure which is right for your machine is to pick up a handful of assorted 256 memory sticks (must be double-sided), and try 'em one at a time. Luckily they are cheap enough to buy these days.  
Take a look at: [http://forums.techguy.org/hardware/786616-solved-dell-gx1-memory.html#post6388588](http://forums.techguy.org/hardware/786616-solved-dell-gx1-memory.html#post6388588)  for some further info on this.

Although you don't mention upgrading the CPU, other users might be - so stay with A07 bios should you be planning to use a Slocket to increase the CPU speed. At this stage I can't say for sure whether a Slocket with on-card voltage adjustment is mandatory for the GX1, at least one site: [http://www.angelfire.com/wy/DellOPTIPLEX/GX1.htm](http://www.angelfire.com/wy/DellOPTIPLEX/GX1.htm) suggests not, but I'm a tad leery about installing a 1.75v processor on a board which normally runs a 2.0v CPU.  I do have a spare Celeron which I might install as a 'sacrifical' processor to test the m/board's cpu voltage regulation - I'll let you know if this happens.

---

### Post by adamlau on 2009-01-26
So then pick up three sticks of Crucial CT209821/CT209822 and go with a Xubuntu install to help speed things along :) .

---

### Post by SAE140 on 2009-01-27
> **SAE140 said:**
> I'm a tad leery about installing a 1.75v processor on a board which normally runs a 2.0v CPU.  I do have a spare Celeron which I might install as a 'sacrifical' processor to test the m/board's cpu voltage regulation - I'll let you know if this happens.
I installed a Celeron 900 into the GX1 via a Super Slocket III last night, with a DVM connected between Vcore and Vss. The Vcore was measured at 1.72v, so I can confirm that the m/board does have suitable voltage regulation.  The Celeron doubled the GX1's performance according to SiSoft's Sandra, for very little money.

Also - suggest you avoid using PC133 memory with the GX1. You'd think that if PC100 memory sticks work ok, then PC133 would walk it .... but not necessarily.  Some manufacturers achieve the higher speed rating by using unbuffered chips - having no buffers makes these chips faster, but at the expense of loading the address and data lines far more than their buffered cousins, especially if double-sided sticks are used. So - as counter-intuitive as it sounds - PC100 sticks may work where PC133 will not. I've tried Crucial d/sided 133, and these wouldn't work for me, where unbranded PC100's did.

---

### Post by gusteman on 2010-05-16
Well, many thanks to all you guys, but since in the mean time I have replaced the Optiplex GX, this thread no longer has any use for me.
At least not for the time being.
I still have the machine set aside so I might consider upgrading it a little bit and then give it to one of my kids.
The info you provided certainly is really interesting and helpful.
So in the mean time I can mark this thread as SOLVED.

---

