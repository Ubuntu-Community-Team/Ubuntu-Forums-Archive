---
title: "new cpu, overclocking, and freezes."
date: 2009-05-29
forum: General Help
---

### Post by Bigneil on 2009-05-29
Hi, i have an old pc.. i refuse to give it up since i have done so much to it over the years, i just keep upgrading as much as possible... it's like an old friend.

i recently dicovered that i can now buy second hand cpus that blow the pants off my old one for a very reasonable price. so i bought one installed it, got it running, i then started tweeking about with bus speeds and multipliers until i had it running to its fullest potential that my motherboard and heat managment could stand. everything worked fine under XP (all the monitoring tools are there) but when i tried to boot into Ubuntu the system lasted about 3 seconds then froze so i rebooted and the same thing happened. So, i tweeked the clock speed back down to standard and all was working again.  

How come i cant clock the thing up a bit in Ubuntu?



via kt-600 chipset  amd athlon 3300+  

I was able to run it at 133MHz  266MHz fsb with the multiplier at 15x giving me 2Gig i tweeked up the speed in BIOS to 150MHz 300 fsb and it worked fine in xp yielding a respectable 2.25Gig. but i had to turn the clock back down to 133MHz for ubuntu.


are there any experienced overclockers using ubuntu??  

neil

---

### Post by Bigneil on 2009-05-30
BUMP!

the CPU is actually a 2400+ that yields 2 gig on 133MHz (266 FSB) but can be effectivly used as what would be a 3300+.  

when i tweek up the frequency in BIOS up from 133, my ubuntu doesnt work.  any one have any ideas?

---

### Post by mcduck on 2009-05-30
Linux tends to be more sensitive about incorrectly working hardware than Windows is. It usually stops working as soon as things start going wrong, while Windows keeps on working but corrupts your data over time..

150MHz FSB is quite a lot for that setup, while the CU definitely can take it with a bit of tweaking make sure your memory can do the same. Also, VIA chipsets sure aren't the best ones for overclocking.

Anyway, increase the FSB bit by bit and test how far you can get. When the system becomes unstable drop the speed back a bit and let the machine run some CPU-intensive task overnight. If that works, you can keep on using that speed. If it smallest of a problem drop the speed a bit more & try again.

---

