---
title: "Upgrading to Nvidia"
date: 2009-07-06
forum: Gaming &amp; Leisure
---

### Post by Da CalebMan on 2009-07-06
Hey Guys,;)

Could anyone tell me what type of Nvidia GPU they think is best for Ubuntu 9.04??
I'd like to upgrade my Intel integrated extreme graphics to a more Linux compatible GPU...

Does anyone have some suggestions for which GPUs are most Linux compatible, can play okay games, and is priced under $40 bucks?

Thanks!

Da new guy...:lolflag:

---

### Post by tommcd on 2009-07-06
Just about any nvidia card will work. Here is the list of officially supported nvidia cards from the Ubuntu wiki:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)
Also, if you open a terminal and run:
```
aptitude show nvidia-glx-180
```
 you will see a long list of all the the nvidia cards that the driver supports.
As a  general rule, the latest and greatest nvidia cards will require the most recent drivers from nvidia. It can take a while before these drivers make it into the Ubuntu repos. Slightly older nvidia cards are usually better supported.

As for price, the nvidia 6000 and 7000 series cards and some of the 8000 series cards will fall in that price range. I have an nvidia 7300GT. It works fine in linux. It is powerful enough to play FEAR2 and "Call of Duty, Modern Warfare" just fine on Windows XP with all the effects turned down to minimum.

---

### Post by X-BANE on 2009-07-06
A GeForce 8600GT if you have a PCI-e slot, or a GeForce 7300GT if you have a AGP slot.

---

### Post by Da CalebMan on 2009-07-10
Thanks guys!

Only problem is, I have no PCI-E slots...

Only PCI and AGP, and I'm not sure which type of AGP version that is...

How do you tell?

I am willing to open up my computer case and take a look. Or can U simply type a terminal command?

Thanks a bunch!

~Me...

---

### Post by Da CalebMan on 2009-07-10
The 7300GT sounds nice, 

It might be a little new for my motherboard though (HP D300 DT, Business)

It's a second hand, and I'd really like to make my own just for gaming...

---

### Post by Sockerdrickan on 2009-07-10
**NO **do not get any of the 7-series buy 8-series or later. OpenGL 3.1 hardware support starts with 8-series

---

### Post by tommcd on 2009-07-10
> **Da CalebMan said:**
> 
Only PCI and AGP, and I'm not sure which type of AGP version that is...
How do you tell?

See this tutorial:
[http://www.hardwaresecrets.com/article/155/3](http://www.hardwaresecrets.com/article/155/3)
> 
In August, 1998 a new specification of the AGP bus was launched: AGP Pro. AGP Pro defined a larger slot, with more voltage pins, for high-consumption 3D video cards. The AGP Pro slot is compatible with the previous versions of the AGP bus, in other words, you can install conventional 1.5 V or 3.3 V AGP video cards in AGP Pro slots.

So if your motherboard was made after 1998 you should be able to install any available AGP card in your AGP slot without a problem.

Another thing to consider is that a 7300GT AGP card will require a 4 pin molex power connector from your computer's power supply in order to function. See the pictures for the 7300GT here:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814143102](http://www.newegg.com/Product/Product.aspx?Item=N82E16814143102)
So if you get a 7300GT, make sure you have a spare molex connector from your power supply to plug into the card. You could get a nvidia 6200, which does not require a separate power connector to work:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814150107](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150107)
EDIT: I don't know if nvidia 8000 series cards are available for the AGP slot. See this:
[http://forums.nvidia.com/lofiversion/index.php?t39902.html](http://forums.nvidia.com/lofiversion/index.php?t39902.html)

---

### Post by khelben1979 on 2009-07-21
> **Tux0r said:**
> **NO **do not get any of the 7-series buy 8-series or later. OpenGL 3.1 hardware support starts with 8-series

I found this very interesting! I have an nVidia Geforce 7800 GS graphic card over here.

Exactly, what does it mean that hardware support begins with the 8-series? For example, do the newer technologies in the latest line of graphic cards get fully utilized by the latest OpenGL 3.1?

---

### Post by Sockerdrickan on 2009-07-21
> **khelben1979 said:**
> I found this very interesting! I have an nVidia Geforce 7800 GS graphic card over here.

Exactly, what does it mean that hardware support begins with the 8-series? For example, do the newer technologies in the latest line of graphic cards get fully utilized by the latest OpenGL 3.1?
GeForce 8 had a major architecture redesign of the GPU (G80) with the unified shaders approach and such. Starting from there the GPU became more programmable and so OpenGL 3.1 was written in a way to take advantage of this. To the programmer this means more control of the rendering pipeline. :popcorn:

In the next coming versions modern GPU architecture will most likely blend into new functions, but you can use extensions now already (vendor specific) to access some sweet stuff like nVidias bindless graphics... :)

---

### Post by ztmike on 2009-07-21
> **Da CalebMan said:**
> Thanks guys!

Only problem is, I have no PCI-E slots...

Only PCI and AGP, and I'm not sure which type of AGP version that is...

If you don't have a PCI-E slot...you should really just buy a new computer. You can find a decent one on Newegg.com for cheap then just upgrade its GPU and PSU...This is considering if you don't know how to build a computer from scratch (which would be cheaper and better in the long run.)

I bought a 8800GT for $75 ..used but in excellent working condition. (Which is a PCI-E slot card) but plays newer games pretty well for its age.

---

### Post by accLinux on 2009-07-21
> **Da CalebMan said:**
> Thanks guys!

Only problem is, I have no PCI-E slots...

Only PCI and AGP, and I'm not sure which type of AGP version that is...

How do you tell?

I am willing to open up my computer case and take a look. Or can U simply type a terminal command?

Thanks a bunch!

~Me...


I have the same problem, no pci-e slots. And not enough money for a new pc
(And my parents will not buy me one) So I ended up with a regular pci card, the EVGA GeForce 8400 GS Video Card - 512MB DDR2, PCI, DVI, VGA, HDTV. link:   [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4410190&CatId=319](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4410190&CatId=319)




Its currently $54.99 at TigerDirect, so its not too much. Not top of the line but will play Crysis reasonably at all low settings. Plays all the linux games fine at lower settings too: alien arena 2k9 lowest settings at 75fps low settings at 35fps, highest settings at about 18fps (you might very well get higher fps, my old P4 Processor is holding my gpu back) Gets 90fps on all max setings in tremulous (but that an old game)

Works well for my computer, probably any Nvidia 8000 series card would work well.

---

### Post by Wally_dog on 2009-07-22
If you are able to spend around $600-650 (excluding speakers, monitor, keyboard, mouse), you could build the rig I have. Here are the parts, and everything was bought off newegg.com.

Case: Apevia X-Plorer (non-PSU version)
PSU: Corsair 650TX
Motherboard: Asus P5QL-Pro
CPU: Intel Core 2 Quad Q6600
RAM: Corsair XMS2 DDR2 800 (2x2GB kit)
GPU: MSI nVidia GeForce 9800GT OC
HDD: Western Digital Caviar 250GB 7200RPM 16MB cache
CPU Heatsink: Sunbeam Core Contact Freezer
WiFi card: D-Link WDA 2320

Everything is working perfectly under Jaunty right now. This rig can handle next to anything I throw at it without lag. I can even play Crysis at all High settings, without lag. The CPU heatsink I bought is only because I have my Q6600 overclocked to 3.4GHz, so it needed something to keep it very cool :)

---

### Post by Ericj1186 on 2009-07-22
Under $40?  I can't think of too many video cards that are worthwhile, but I will say anything done by BFG Technologies (they produce Nvidia cards and offer a lifetime warranty) is worth getting.  I have two Nvidia GTS 250 by BFG, and after a bit of fighting, they are running great.

What games did you say you wanted to play?  Any?  Certain ones?  That will help.

---

### Post by snargfish on 2009-07-22
I have a gForce 9500gt and it works really well!

---

### Post by Sockerdrickan on 2009-07-23
> **snargfish said:**
> I have a gForce 9500gt and it works really well!
Of course it does, it's an nVidia :popcorn:

---

