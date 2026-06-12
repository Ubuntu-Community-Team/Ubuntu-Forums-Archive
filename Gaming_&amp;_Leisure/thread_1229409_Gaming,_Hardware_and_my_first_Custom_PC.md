---
title: "Gaming, Hardware and my first Custom PC"
date: 2009-08-02
forum: Gaming &amp; Leisure
---

### Post by billdotson on 2009-08-02
So, about 3 years ago I built my own PC. Since I have upgraded the power supply and the video card so those in the list aren't the original. Regardless, I am going to stick the order invoice in pastebin so you can see it. The current video card and PSU are below the pastebin link. I was going to build this for a gaming PC and try to get a good one for as cheap as possible. How do you think I did? I heard that since the core 2 duo has a quad pumped FSB that its FSB (since it is 1066MHz) is around 266Mhz. That means that I got RAM that was too fast right, since the DDR2 is 400MHz FSB (dual data or something). However, I have also heard that RAM and FSB don't always have to be a perfect match and that sometimes higher speed RAM can still operate due to something. Is that accurate? Are there any other parts I kinda messed up on? Oh yeah, I bought a cheap 5.1 speaker system too. Also, I don't understand all the stuff you need to know if the RAM is compatible. I kinda know bus speed and # of pins but don't know about latencies, etc. I have always heard it is just a good idea to buy the exact same RAM from the same manufacturer and just get however many sticks you need.

The specifications are: [http://paste.ubuntu.com/243357/]("http://paste.ubuntu.com/243357/")

Here is a link to the Zalman copper heatsink/fan: [http://www.newegg.com/Product/Product.aspx?Item=N82E16835118115]("http://www.newegg.com/Product/Product.aspx?Item=N82E16835118115")
- PSU: Antec Truepower Trio 550watts [http://www.antec.com/Believe_it/product.php?id=NjE=]("http://www.antec.com/Believe_it/product.php?id=NjE=")
- Video card: Gigabyte nVidia GeForce 8800GT 512MB

The case has a 120mm fan on the back, a 120mm fan on the side and two 80mm fans in the front (but only one may be working). Side question: what is the "Arctic Silver 5 Thermal Compound - OEM" used for with the CPU specifically?

Anyway, here is the discussion part: Is it really necessary these days to have anything more powerful than what I have now? This question does not include video editing, modeling, drafting, etc., only playing games on a PC. I have seen some of the new stuff Intel and nVidia has and it is ridiculous. The i7 processors and the 200 series of graphics cards sound amazingly powerful. The DDR3 Ram running at 1600MHz or so is ridiculous too. 

But really though, has there been ANY other PC game since Crysis, with the exception of a handful like Supreme Commander (with multiple players) that requires anything that beefy? There are videos out there: [http://www.youtube.com/watch?v=apV8B_Vxf_I]("http://www.youtube.com/watch?v=apV8B_Vxf_I") that show what Crysis looks like with this natural mod and yes, it looks very good, but the thing is is that most people don't have a monitor that does 1600x1200 or the crazy 1920x1080 monitors. I have even seen one with higher than that: [http://accessories.us.dell.com/sna/category.aspx?c=us&category_id=6761&cs=19&l=en&s=dhs&~ck=anav&nf=4723~0~382981&navla=4723~0~382981]("http://accessories.us.dell.com/sna/category.aspx?c=us&category_id=6761&cs=19&l=en&s=dhs&~ck=anav&nf=4723~0~382981&navla=4723~0~382981") 

If there is a game that requires more than Crysis, I haven't heard of it. In fact, I saw some other hardware hogs being discussed on gamespot and I believe Crysis was basically the only game above "OK" that needed that much hardware. So in about 2 years the hardware has been getting so much better but we still have very few games getting more than 2 core support and we haven't had any good games require that much power since Crysis (as far as I know).

With my updated PSU and video card I was running Crysis at medium/high and sometimes high (some Vista functionality too I believe). I don't think there would be any need for me to update any part of my system at this point in time, except for crappy keyboard.

---

### Post by arcdrag on 2009-08-02
I've got roughly the same rig as you.  You can play pretty much any game out there on medium graphics with that rig on a 19" monitor.  Personally, I'm going ahead and upgrading from 2gb ram to 4gb (roughly $30)...but I don't plan on doing any other upgrades until I build my 64 bit system sometime next year.

---

### Post by billdotson on 2009-08-03
I am almost certain that without doing something special you aren't going to have a 32 bit operating system recognize all 4gb of RAM. I believe it will only recognize 3-3.3GB. If you have an intel core 2 duo and the same motherboard as me I believe the processor can be used as a 64 bit processor as well. Might be some other things that don't work though. Really though, I don't think there are very many games are even out there for 64 bit so unless you could install a 32 bit os on a 64 bit computer and dual boot or whatever-boot you would probably be doing yourself a disservice.

Anybody else have any thoughts on how there really haven't been any games that have really required as much hardware as everyone was saying they would? What about my mistake with my RAM?

---

### Post by arcdrag on 2009-08-04
I know it won't recognize all of it, and I'm not really concerned.  DDR2 RAM is so crazily cheap right now that I'm not worried if I utilize all of that last stick.  You're right, I could install a 64 bit OS, but I just don't see a point yet. Most gaming has to be done in Windows, and I don't see any advantage to be gained from spending $100-$200 on a 64 bit windows license right now.  

Right now hardware is outpacing software that can utilize it.  64 bit systems are only now beginning to rise in popularity.  Since many big name games spend 4-5 years in production, I think it may be quite a while before you see anything that requires a 64 bit system.  The only reason I'm upgrading my RAM at all is because a Windows 7 VM with Visual Studio does not run as smoothly as I would like.

---

### Post by Zenki on 2009-10-20
Ok so I have some comments on your hardware woes.
 
As far as 32/64-bit computing goes, even a 32 bit OS operating on a 64-bit processor will process faster than an identical 32 bit chip. The advantages of a 64 bit OS are more utilization of the cores, memory and bus speeds.
 
You have some misconceptions about the FSB. Your FSB is the advertised speed *outside* of the processor. That is its communications speed with the Northbridge and thus RAM HDD VGA etc. It is split *on die,* meaning that the bus speed is slower on chip, but the architecture compensates for this (quad pumping).
 
When buying ram you should pick the best ratio between FSB and RAM clock speed. So if your bus speed is 1066Mhz you should by 1066Mhz RAM, 1:1 ratio acheived (ddr3 or ddr2). Or in the case of an old computer i have 800Mhz FSB and 400Mhz RAM 1:2 ratio.
 
However, nowadays the L3 cache has swelled so much that the chances of a cache miss are less than 1% which means that RAM matching is less important than it used to be.
 
IMO you should splurge on a 64 bit OS since you cant even buy a new 32 bit processor anymore. If you are worried about 64 bit applications being rare, consider that Windows just released a 64 bit Internet explorer. This should tell you that this is catching on, and catching on fast.
 
Arctic silver 5 is a thermal compound.  It is used to "bridge the gap" between the CPU heatsink (the part that you can see) with the contact plate on the cooler. It is composed of silver atoms and some other inert compounds that are designed to deliver the maximum amount of energy (heat) from the heatsink to the contact plate.  The energy is then free to travel through the contact plate to the rest of the cooler and thus be dissipated.  If you did not use a thermal compound the heat would not transfer nearly as well, or at all, and render the cooler useless.  Arctic silver is the best there is, you get plenty so lather it on, just make sure it does not touch the PCB cause it will transfer electricity. 
 
Heres what i bought about a year ago.
AMD Phenom 9850 2.5Ghz quad core
ATI HD4850 512MB Graphics
MSI K9A2 Platinum w/AMD790FX NB Motherboard
WD 600GB 7200RPM HDD 16MB cache SATA 3.0
Corsair 4GB DDR2 1066 RAM w/cooler
Kingwin 1000w Modular PSU (a bit overkill, but will handle expansion)
Antec 1200 case.
Acer 22 Inch Widescreen 5ms monitor
64 bit Windows Vista Ultimate.
Less than $1000.00
 
BTW I love Apeiva cases, but antec really makes a better case.
 
Lastly, here are some tips when you build again.
1. Use Newegg.
2. Make use of free shipping, everything I bought was FS and i saved more than $100.00.
3. Combo deals can be your enemy, sometimes the items are not compatible, check for compatibility, otherwize they are your best friend.
4. Buy all at once and dont wait for new tech to come out, its always advancing so whatever you buy will ALWAYS be obsolete.
 
Good luck in your future builds!

---

