---
title: "how do i install ATI drivers for Jaunty?"
date: 2009-05-09
forum: General Help
---

### Post by ihaveabu on 2009-05-09
I'm sport an old school Radeon 9600 on my front desk computer. ubuntu works fine without the drivers, but i was told i would run faster with it. 

so i went on ati.com and downloaded this .bin file for the radeon 9600.

how do i install this? i'm new at ubuntu thanks everyone

---

### Post by Triptol on 2009-05-09
It is easier to install them the "Ubuntu way". From a terminal (or press alt+F2) you enter 
```
jockey-gtk
```

or 

```
jockey-kde
```

The first one if you are running Ubuntu, the second in case your are running Kubuntu. From here you should be able to install the ATI drivers in an easy way.

---

### Post by ihaveabu on 2009-05-09
> **Triptol said:**
> It is easier to install them the "Ubuntu way". From a terminal (or press alt+F2) you enter 
```
jockey-gtk
```or 

```
jockey-kde
```The first one if you are running Ubuntu, the second in case your are running Kubuntu. From here you should be able to install the ATI drivers in an easy way.

this is what i get when i tried that:
see attachment

---

### Post by Dimarchi on 2009-05-09
Ati driver that supports the 9600 series video card that you have does not exist in Jaunty. You should use the one that worked when you installed Jaunty (either xserver-xorg-video-ati or xserver-video-xorg-radeon, I guess). The screenshot in the attachment displays the correct response, therefore.

Do not attempt to install the driver you have downloaded. It will bring you only misery.

---

### Post by ihaveabu on 2009-05-09
> > **Dimarchi said:**
> Ati driver that supports the 9600 series video card that you have does not exist in Jaunty. You should use the one that worked when you installed Jaunty (either xserver-xorg-video-ati or xserver-video-xorg-radeon, I guess). The screenshot in the attachment displays the correct response, therefore.

Do not attempt to install the driver you have downloaded. It will bring you only misery.

i never actually installed any display drivers. i'm running ubuntu right now without any manually installed drivers. should i install a driver then, if the one from ati.com is not made for jaunty?

---

### Post by lvleph on 2009-05-09
I have found the envy-ng is the best tool for install video drivers.

---

### Post by b@sh_n3rd on 2009-05-09
> **Dimarchi said:**
> Ati driver that supports the 9600 series video card that you have does not exist in Jaunty. You should use the one that worked when you installed Jaunty (either xserver-xorg-video-ati or xserver-video-xorg-radeon, I guess). The screenshot in the attachment displays the correct response, therefore.

Do not attempt to install the driver you have downloaded. It will bring you only misery.

Sorry if I'm out of topic. Does this mean that if I assemble a PC with an Integrated ATI vid. card I'm an idiot??. If you say yes, I choose nForce 980a SLI. If you say no, I choose AMD 970FX/970GX :D.

---

### Post by mossman44 on 2009-05-09
Use these instructions: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by ihaveabu on 2009-05-09
> **lvleph said:**
> I have found the envy-ng is the best tool for install video drivers.

this is what i get when i installe envyng:

---

### Post by ihaveabu on 2009-05-09
this is bad huh:
> I guess the rest of the guide is broken or it may be because the new driver doesn't support any of the older ATI cards anymore. Which cards does ATI no longer support? *The ATI Radeon 9500-9800,X300-X2100,Xpress.  See the complete list [[1]]("http://wiki.cchtml.com/index.php/9.4") here.*If your card is on that list, you are restricted to the 9.3 driver - however since 9.3 driver doesn't support xorg-xserver 1.6, it will not work with Jaunty! This guide currently is for installing 9.4. !!!SO BE CAREFUL!!!

what driver version can i install??

---

### Post by ihaveabu on 2009-05-09
this is interesting:
[https://help.ubuntu.com/community/RadeonDriver#Testing%20The%20Driver](https://help.ubuntu.com/community/RadeonDriver#Testing%20The%20Driver)

when i test my drivers, i get the SGI for opengl and Direct Rendering says Yes...

---

### Post by Woody1987 on 2009-05-09
Your card is no longer supported by ATI. It will NOT work on jaunty with the drivers from the ATI website. When you installed Ubuntu it will have installed automatically the driver you need. The driver you already have installed has full 2d and 3d acceleration with your card. No need to change it.

---

### Post by ihaveabu on 2009-05-09
ahh i see. ok that's fine with me

---

### Post by Dimarchi on 2009-05-09
> **b@sh_n3rd said:**
> Sorry if I'm out of topic. Does this mean that if I assemble a PC with an Integrated ATI vid. card I'm an idiot??. If you say yes, I choose nForce 980a SLI. If you say no, I choose AMD 970FX/970GX :D.

Choose the one you like. After all, it is you who have to live with it. :) Who am I to dictate what you should select? :) If I'm to suggest something, it is to browse the forum or Google for the subjects that interest you (e.g. video playback, Ubuntu, and Ati...compiz and Nvidia, etc.) and make your decision based on those comments you see. That should give you some background when making the selection.

My newer computer has an Ati 4870 board, so I'm covered there - I can get Ati supplied drivers for it should I need them. My older computer has an Ati 9600 Pro, so no Jaunty with Ati supplied drivers for that. It will work without those drivers, anyway - as Woody1987 says.

Whoever makes the video card (or motherboard, or whatever), you'll encounter something that you do not like, sooner or later...that card works better than this card, this card has features available that that card does not have. These drivers work. Those drivers are buggy.

---

### Post by b@sh_n3rd on 2009-05-10
Okeydokey Dimarchi, I'm stuck with that selection for a PC, coz I'm gonna use Ubuntu as primary OS :D. Karmic Koala maybe...

---

