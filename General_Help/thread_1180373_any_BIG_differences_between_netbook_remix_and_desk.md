---
title: "any BIG differences between netbook remix and desktop ubuntu?"
date: 2009-06-06
forum: General Help
---

### Post by cody7002002 on 2009-06-06
I've been using netbook remix on my asus eeepc 1000he for about a month now and I'm running into a lot more bugs than I have on my desktop running jaunty. I'm thinking about abandoning netbook remix and just installing the full ubuntu on my netbook. Would I have any performance issues running it? Would the eeepc be able to run compiz? I've tried running it on NBR (im using the normal ubuntu desktop configuration) but for whatever reason the effects won't work.

---

### Post by aysiu on 2009-06-07
Compiz runs just fine with regular Ubuntu.

The only difference between UNR and Ubuntu is the netbook remix interface and applications automatically maximizing.

---

### Post by cody7002002 on 2009-06-07
I see. Well do you think compiz would run smoothly on my netbook?

---

### Post by aysiu on 2009-06-07
> **cody7002002 said:**
> I see. Well do you think compiz would run smoothly on my netbook?
If you don't have too many effects, it should run smoothly.

System > Preferences > Appearance > Desktop Effects has three options. The middle one works well on the two netbooks I've had (the Eee 701 and the HP Mini 1120nr). The last one may not run as smoothly.

---

### Post by jonathanysp on 2009-06-07
i have a 1000h which i think is slightly slower than 1000he? not sure about the difference but i use desktop ubuntu which works perfectly. Compiz works smoothly. I actually prefer ubuntu desktop cause it makes my eee feel more of a computer than a internet device.

---

### Post by cody7002002 on 2009-06-07
I put on the extra effects and its running quite well. So is it worth installing desktop ubuntu and getting rid of NBR? Are there no performance issues between the two?

I can't get compiz to work on NBR =/

---

### Post by jonathanysp on 2009-06-07
umm for me i dont find much difference but i havent used NBR extensively. Its your choice and its pretty easy to reinstall if you dont like it. Yea compiz doesnt work on NBR cause you have to use metacity for some reason to get the menu thing working.

---

### Post by blueridgedog on 2009-06-07
> **aysiu said:**
> The only difference between UNR and Ubuntu is the netbook remix interface and applications automatically maximizing.

I thought the UNR used a different kernel.  Is it the same?

---

### Post by meeples on 2009-06-07
as far as ive been able to tell its just regular ubuntu with a launcher and stupid maximizer which i hate.

i think the ubuntu moblin remix will be more worth gettin when it eventually comes out :)

---

### Post by cody7002002 on 2009-06-07
so is there anyway to change from NBR to normal ubuntu  without a complete reinstall?

---

### Post by aysiu on 2009-06-07
> **blueridgedog said:**
> I thought the UNR used a different kernel.  Is it the same?
Yes, it's the same:
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/366025](https://bugs.launchpad.net/ubuntu-cdimage/+bug/366025)

---

### Post by jonathanysp on 2009-06-07
i think there is a desktop switcher included with the NBR it should be somewhere in the preferences.

---

### Post by cody7002002 on 2009-06-07
I know about the desktop switcher im using the "classic" ubuntu desktop. I guess the only thing I want to do that I can't is use compiz. So how can I get that to work on NBR. What's metacity do?

---

### Post by JamesSmith on 2009-06-08
you can run compiz on your netbook. It doesn't work well with the netbook desktop but if you switch to the classic desktop it runs fine.

get "compizconfig-settings-manager" with the synaptic package manager (in System > Administration).

i have the visual effects set to extra in the appearance options and have prevented "maximus" from running at startup (System > Preferences > Startup Apps) which would force all of your windows to open up maximised and makes them skip around when you're in them.

i have lots of the compiz features switched on, like animations, wobbly windows, minimise effect, desktop cube, taskbar previews etc. and it runs ok.  i suppose it eats the battery more and slows things down a bit, but for a regular windows user it's no bother!

cheers

---

### Post by GeorgeVita on 2009-06-09
Hi to all!
I have a 1000H and I would like to share an idea which began "for fun" but remain as a stable point for me!

You can boot from a Live USB stick and then install 9.04 Desktop into a fast **SDHC** card (I used a SanDisk 8GB Extreme III). Use **ext2** format and the result will be "usable". Slower comparing with the HD but you can run WITHOUT the Hard Disk (cooler and extended time).

You can see a "speed compare" at: [http://acomelectronics.com/GeorgeVita/extPoll.jpg](http://acomelectronics.com/GeorgeVita/extPoll.jpg)
(the procedure I used: [http://acomelectronics.com/GeorgeVita/Gdsk_bnch.txt](http://acomelectronics.com/GeorgeVita/Gdsk_bnch.txt))

If you like to test various versions (I have lxde, puppy, 8.10, 9.04) this is the way. Do not fear about "life expectancy" of the card as ... till it breaks we would have 64GB to buy at a same price!

Regards,
George

---

### Post by blueridgedog on 2009-06-09
It would be nice to see SSD numbers as well.  My Asus has two SSD drives standard.

---

### Post by GeorgeVita on 2009-06-09
Hi **blueridgedog**,
I would like to test a real SSD but I do not have one!

Would you like to do my test to your netbook? I wrote a "preliminary" note at:
[http://acomelectronics.com/GeorgeVita/Gdsk_bnch.txt](http://acomelectronics.com/GeorgeVita/Gdsk_bnch.txt)

The idea is to form a directory with some files (1200MB total size) and test copy from/to the same media (using **time cp -r /media/.../* /media/...**). Then divide 1200MB by the "real timing" in seconds and you have the aprox. MB/s (real files not min/max).

G

---

