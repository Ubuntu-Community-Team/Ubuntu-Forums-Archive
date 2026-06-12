---
title: "Dell Inspiron 1100, overheating?"
date: 2011-07-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by goodbye-windows(tm) on 2011-07-19
Hi All,

I'm new to Linux, but have followed the movement for years. I finally decided the time was right to give windoze the boot.

My laptop has always been horribly slow-by anyones standards, whether in windoze or in Linux. Yesterday I figured out how to check the processor temp.

My system is a Dell Inspiron 1100, dual boot running Xubuntu 11.04. It has 760 MB of ram. It will not play videos on youtube without skips in the video and sound, although it does a little better with Xubuntu than it does in Ubuntu. The fan always runs, it's very noisy-it comes on almost immediately at boot up and never seems to slow down.

I determined the processor utilization is high, even after a fresh boot. After a fresh boot, I see the processor temp running about 165F, with a note on the screen that the critical temp is 172F. I took a screen capture and attached it. Note that this screen capture was taken after a fresh boot, with only the sensors software running in command line, with the only other program being the Task Manager.

I think the processor is running to hot and the computer might be slowing down the clocking rate internally, which might explain the really poor performance.

The laptop feels hot, very hot!!! Again, I am not quite sure what is normal and what is not.

I'd appreciate knowing if the temperature is excessive, and if so, what should it be?

Next I plan to check the clocking rate, which will let me know whether the computer is slowing down intentionally, by design...due to the high processor temps.

Comments please-and thanks to all.

Regards,

Art

---

### Post by goodbye-windows(tm) on 2011-07-21
Problem is solved.

I took the cooling fan and the processor out. I found Dell had only applied thermal compound to half of the mating surfaces (heat sink and microprocessor)

Dell also use the generic white thermal compound, which is marginal at best.

I did not find any major amount of dust internally, so no cleanup was performed.

I found the microprocessor was loose in it's socket, and suspect Dell did not tighten the screw on the zif processor socket during the original assembly.

I did put the good thermal compound on the microprocessor to heat sink junction and reassembled the laptop. 

I now find the fan runs at slow speeds and the exterior of the unit feels slightly warm instead of hot. The highest observed microprocessor temperatue is 146 degres F, which only happens during an extended period of 100 percent processor utilization. In the past, this temperature would be in the 160 degree range with very light processor loads.

It's a pleasure to use the computer now, it runs much faster and the fan runs occasionally on low speed instead of being maxed out constantly.

So, it is fixed and I couldn't be happier with the results!! GO UBUNTU!!!!!!

Art

---

