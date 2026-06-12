---
title: "Wrong resolution on Dell OptiPlex 745 ( Ubuntu 11.10 )!"
date: 2012-05-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by EMiiRU on 2012-05-01
Heya.. I've looked around the forums, but this problem is different ( and quite awkward )..

So, my PC ( Dell OptiPlex 745 ) doesn't have a VGA port, and I bought a 23' inch TV with does have a VGA port, and a HDMI port.. so, I got a DVI to HDMI cable ( one side DVI one side HDMI ) and connected my PC to the TV, now.. the awkward problem is.. on Ubuntu and Kubuntu 10.10 it detects the 1920x1080 resolution, but on Ubuntu 11.10 the maximum resolution which I can choose which is "1360x768 ( Auto )" indeed blurry, and I can't set a resolution higher than that unfortunately :(

My question is, how is it possible for Ubuntu 11.10 to have the wrong resolution while 10.10 just worked fine, and how can I fix that, haven't found other people having this problem..

My video card DOES support that resolution ( Intel video card, I'll give you more details if you want, can't atm ).. as it works fine in Windows 7, Windows Vista, Ubuntu 10.10 and Kubuntu 10.10.. it's just the new versions of Ubuntu I'm having resolution problems with.. I also encountered this problem in Linux Mint.. ( not relevant, just a quick fact hehe )..

Monitor is detected, ( as DVI1 ).. in case it's any useful information..

Sorry for complete noobishness, I'm not really new to Linux, it's just this weird problem that keeps bugging me.. haha

Any ideas? :confused:

---

### Post by EMiiRU on 2012-05-04
Yup, fixed it.. what I did was using xrandr in Terminal to get the right resolution.. 

```
gtf 1920 1080 60 ( horizontal, vertical resolution and Hz )

xrandr --newmode "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync

xrandr --addmode DVI1 1920x1080_60.00

xrandr --output DVI1 --mode 1920x1080_60.00
```Does anyone know how to make the changes pemament?

---

