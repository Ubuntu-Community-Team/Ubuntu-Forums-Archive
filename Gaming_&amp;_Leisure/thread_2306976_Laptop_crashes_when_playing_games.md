---
title: "Laptop crashes when playing games"
date: 2015-12-20
forum: Gaming &amp; Leisure
---

### Post by mike1772 on 2015-12-20
I've been having problems with games for some time.  I have an HP Envy 17 laptop with AMD 5800 graphics that used to work for games.  It's quite likely my issue is hardware and not software - if it is Ubuntu it is very coincidental as I have issues under windows 10 as well.  My laptop always ran hot - I've been monitoring the temperature of the video card and it's been running around 78C - as high as 90C when actually in use.  I still seem to be able to play pillars of eternity (under Linux - fails under Windows) though it does freeze sometimes.  Sword coast legends freezes during character creation or after but before getting into the game proper.  Witcher 2 also freezes before I get in but it used to work (before Ubuntu 15.10).  

However, since the upgrade to Windows 10 I get display adapter has stopped responding and has restarted when trying under windows as well.  Since both OS's have been upgraded it's entirely possible they are both having similar but unrelated problems but I fear it's a damaged video card.  I have tried various drivers under both OS's including current and beta catalyst under windows and the same under Linux as well as the open source drivers.  Some games actually ran better under Ubuntu 15.04 with the open source drivers but since the upgrade nothing seems to run well with them.

I bought a fan to place under the laptop (it's 4 years old so I'm closing the gate after the horse has left) and the temp is now 63C - lower then I've ever seen it.  When I try to play a game it doesn't go above 80C now - but I still get the freezes. 

Everything else works perfectly under both OS's but nothing else I do really taxes the video Card.  Anyone have any ideas?

---

### Post by anawizowski on 2015-12-20
Try replacing the thermal paste, it helped in my case. GPU temperatures dropped by about 20* Celsius.

---

### Post by mike1772 on 2015-12-20
I've been googling about the mother board as this thing (being a laptop) is a real pain to get apart.  I've had the memory out, the keyboard off, the drives out, network adapter off - but I still couldn't get at the motherboard and find out where on it the GPU is unfortunatly.  This laptop has served me well - but I miss the old days when I had a desktop and this stuff was much easier!  when I get a free hour I'll take it apart and try to find the GPU again.  I have cats as well so I was hoping it was full of cat hair and dust and I could just blow it out but I didn't find any.  Thanks for your quick reply!

One thing to add to my earlier post - thinking (hoping?) it was the memory I removed 4 of the 8 GB and tried again and switched them around to try and isolate bad memory but got the same results. I was hoping as memory is something I could easily replace.

---

### Post by Bucky Ball on 2015-12-20
Do you mean 'C' as in celcius??? If you are getting those temperatures inside the box, expect failure very soon. I'd say nothing to do with software. The recommended max operating temp for a hard drive, or SSD, is half what you are getting: 40C.

There is something seriously wrong if your laptop is telling you 80C. Use the 'Disks' utility in Settings and see what temperature the hard drives are showing. My two drives, on HDD and one SSD, are both showing 32C and never go higher than around 42C (only the hard drive which is about six years old).

Have you blown out vents with compressed air? That may help.

---

### Post by mike1772 on 2015-12-21
CPU and GPU always ran hot on this laptop.  The HHD is currently showing about 31C and the CPU 58C.  GPU is now at 63C.  It's been staying much lower since I put it on a stand with fans under it.  However after about 4 years of really high temperatures I  suspect the GPU has failed.  Odd that it can do all other tasks - just not games though.  

I have blown out all vents with compressed air and I had the entire laptop apart looking for anything else to blow out.  So far no luck.  Thanks for your suggestions.

---

### Post by mike1772 on 2015-12-28
So - just for anyone else having a similar problem - I actually have this laptop playing games again under Ubuntu.  Firstly - I'm using the Open source Radeon drivers - NOT the AMD proprietary drivers.  I got further using this.  Googling around I determined that some people had better luck with DPM off.  After trying this I've been able to play most of my games.  A few need opengl 4.x which I don't think I have with this driver but I'm not really knowledgeable in that area.  

Still no go under windows 10 - not sure if there is a similar setting - but then that is a matter for another forum.  Thanks again for all of your replies.

---

