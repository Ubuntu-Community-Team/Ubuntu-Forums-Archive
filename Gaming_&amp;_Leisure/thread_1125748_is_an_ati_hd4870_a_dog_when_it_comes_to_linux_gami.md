---
title: "is an ati hd4870 a dog when it comes to linux gaming?"
date: 2009-04-14
forum: Gaming &amp; Leisure
---

### Post by larryfroot on 2009-04-14
Hi, just a quickie. Is my choice of an ati hd4870 a bad one when it comes to gaming on linux? I know catalyst 9.3 wont spanner with compositing on anymore, so perhaps gameplay may improve as well? Or should I just use nvidea? Thanks for your time on this one, I just need some advice!

---

### Post by Mokoma on 2009-04-14
> **larryfroot said:**
> Hi, just a quickie. Is my choice of an ati hd4870 a bad one when it comes to gaming on linux? I know catalyst 9.3 wont spanner with compositing on anymore, so perhaps gameplay may improve as well? Or should I just use nvidea? Thanks for your time on this one, I just need some advice!

ati used to suck, but apparently its better now, so i dont know.

---

### Post by rizzeh on 2009-04-14
I second Mokoma. My current system was build with linux in mind so I chose nVidia SLi.
There is also open source ATI driver available, don't know if its any better than the official.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Mokoma on 2009-04-14
i would go with nvidia, but ati drivers are far easier to install than nvidias and that alone may be enough to sway you. theres also the fact that amd have began to focus support for hd2000+ cards in their driver support, so maybe ati wouldnt be the dumb choice it once was for linux :-s

---

### Post by Melcar on 2009-04-14
It's a great card for games.

[http://www.phoronix.com/scan.php?page=article&item=sapphire_4870toxic&num=5]("http://www.phoronix.com/scan.php?page=article&item=sapphire_4870toxic&num=5")
[http://www.phoronix.com/scan.php?page=article&item=ati_radeonhd_4870&num=4]("http://www.phoronix.com/scan.php?page=article&item=ati_radeonhd_4870&num=4")

---

### Post by Izek on 2009-04-14
> **Melcar said:**
> It's a great card for games.

[http://www.phoronix.com/scan.php?page=article&item=sapphire_4870toxic&num=5]("http://www.phoronix.com/scan.php?page=article&item=sapphire_4870toxic&num=5")
[http://www.phoronix.com/scan.php?page=article&item=ati_radeonhd_4870&num=4]("http://www.phoronix.com/scan.php?page=article&item=ati_radeonhd_4870&num=4")

Windows I assume.

---

### Post by Simey on 2009-04-15
> **Izek said:**
> Windows I assume.

Hmmm? Both of those benchmarks were on 8.04.
Also note that in those benchmarks where the 4870 is outperformed by the 9800gtx, the benchmarks are over half a year old, and the ATI driver situation has improved much since then. :-)

---

### Post by khelben1979 on 2009-04-15
If you choose to go with the hd4870, then make sure it has a good cooler on it. These graphic cards get's very hot.

DriverHeaven has a review on of these cards [here]("http://www.driverheaven.net/reviews.php?reviewid=706") if you're interested.

---

### Post by Melcar on 2009-04-15
> **Simey said:**
> Hmmm? Both of those benchmarks were on 8.04.
Also note that in those benchmarks where the 4870 is outperformed by the 9800gtx, the benchmarks are over half a year old, and the ATI driver situation has improved much since then. 



And once you start turning up the AA/AF levels and other post processing effects the situation reverses.  The ATI drivers are really good right now, and if all you do is game or run other 3D apps. even better.  Where they do choke at the moment, and this is due to the changing drivers, is under composite environments; 2D rendering can be a bit choppy, and accelerated video playback (Xv/opengl) can cause problems, but these problems are being worked on (and if you don't use composite managers they are a non issue).

---

### Post by binbash on 2009-04-15
ATI drivers are good now, and going better and better.But i agree with  khelben1979's comment.

---

### Post by larryfroot on 2009-04-15
Thank you all very much for your input! I feel much cheered by the news that my hd4870 can cut to the chase, so to speak. Cooling, I did a full system build including in it the hd4870. When I switched it on for the first time I nearly had a heart attack. It sounded like a bleedin' jet engine as the ati cooler cleared its throat. In the end I settled for a custom cooler from quietpc by scythe. Best thirty quid I ever spent. As an aside, if any of you use a custom cooling solution that in part or in whole uses heat sinks, make sure you stick heatsinks on the voltage regulators. Its not in the instructions to do so, which is an ommision considering that they were reaching temperatures of 110 celcius in use! Heatsinks and fans reduced it to 60 celcius. Under full load my GPU runs at around 65 celcius now. God alone knows what it was reaching before. And its a lot quieter. 

Open source drivers are still lacking in 3D punch (so my research tells me). As far as ati fglrx drivers and compiz goes, I choose X11 as my video output in vlc which really helps video playback, but the latest catalyst drivers are working well with compositing, apparantly. 

Thanks again, will chase those links and am well chuffed how many of you chipped in to help me out. Thank you!

---

### Post by marcgh on 2009-04-15
Hi,
I am using the ATI 4850 for a few months now.
The new ATI catalyst 9.3 solved all of my problems.
Added 1 extra exhaust fan in the case for the cooling.
I'm happy with it, playing whatever I get without problems.
Marc

---

### Post by frodon on 2009-04-15
ATI drivers are just a nightmare to install, especially when the card isn't even recognized without the drivers installed.
Once you get the drivers installed it's great.

Too much pain for too little advantages for me, that's why i bought again an nvidia card last month although i have an HD4870 on my media center and it's a great card (but this computer runs vista).

---

### Post by larryfroot on 2009-04-15
I let ubuntu install the fglrx driver for me, then regreted it when I heard some good things about the catalyst 9.3 drivers. I will just have to use my common sense and synaptic to get back to vesa and install the latest driver manually. Its not that scary. I did it awhile back on a previous install, using the ati linux wiki. But if I can get my games up n running on linux then its the long drop into oblivion for windows for me.

---

### Post by larryfroot on 2009-04-16
Just a heads up, the 9.4 catalyst driver is ready for windows and "will soon be ready for Linux" according to AMD

---

### Post by WalmartSniperLX on 2009-04-16
Interesting. I've been debating on either getting an Nvidia GTS 250 or a AMD ATI Radeon HD4850 or HD4830 based on my budget. Pricewise to performance in general, and considering drivers and support, I'm leaning toward NV. Over the last couple years I've used in linux (in chronological order) a Geforce MX440, Radeon X1600pro, Radeon 9200, Nvidia Geforce 8600GTS, Radeon HD2600pro, and finally my lappy's crappy Ati IGP integrated chipset. 

I've always had HORRIBLE experience with ATI until the HD2600pro. At that point (about last year), AMD cleaned up ATI's act with the drivers. However, working with ATI and their drivers was always a LOOOOONG waiting game. You would have to wait for the next month's release to see if it fixes your issues, and if not, you have to wait another month and so on. ATI has a monthly release cycle due to the demand for a fix for their historically crappy drivers. Nvidia, on the other hand, releases drivers less often, but they are always higher quality. Because of my experience, I don't think that I'll be thinking again about which card to get next to finish my handmedown AM2 barebone...

I'm going with the GTS 250

---

### Post by larryfroot on 2009-04-16
well, it hasn't always been encouraging, rooting around forums and reviews digging up the dirt an ATI...especially as I had already invested in a hd4870! I have sen enough though to consider paying for a cedega subscription and take it from there, especially as I may as well wait for jaunty and a manual install of catalyst 9.4...it hads better be good, or I'm going to throw out all the toys in my pram. 

Good luck with your choice, wallmartSniper. I have a feeling though its not you that needs the luck on this one. Its me! 

If I do get some success with cedega, hd4870 and catalyst 9.4 I will let you guys know. In fact, if its a total dogs dinner, I will let you know too!

---

