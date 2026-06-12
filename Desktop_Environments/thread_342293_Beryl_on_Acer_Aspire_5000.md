---
title: "Beryl on Acer Aspire 5000"
date: 2007-01-19
forum: Desktop Environments
---

### Post by lilBeat on 2007-01-19
Hey guys/girls!


I would like to try 3D desktop on my laptop Acer Aspire 5003WLMi:

[b]
AMD Turion 64 ML32 (1.8GHz) 
SiS M760GX Integrated 3D AGP graphics with 128 MB of VRAM 
512MB DDR[/b] 
80GB Hard Drive 
DVD Dual Layer Drive 
15.4" WXGA Widescreen TFT Screen 
Integrated LAN and 56k v.90 data fax modem 
Integrated wireless 802.11b/g 
3 USB 2.0 Sockets
Ubuntu 6.10 Edgy Eft

I would prefer Beryl but can somebody tell me if it is possible to do it on this system?

P.S.
Wouldn't like to burn something


Thanks

---

### Post by lilBeat on 2007-01-20
I tried Beryl on my system. I installed it following instractions add literam.

While intalling I had a problem:

in xorg.conf did not appear
```

Load       "dbe"

```

Somebody on IRC proposed me to "type in" that line which I did.

I've done all instructed as written at [beryl](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX).


After typing 
```

beryl OR beryl-manager

```
it seems to start beryl, windows change for a second, there is a beryl splash screen for a second and than some errors make xserver killed.

**I would say Beryl/AIGLX does not work on Acer Aspire 5000 (5003WLMi).**

If you have some comment or idea about remediating this problem, please post.


P.S.
I am thinking of bringing system status quo, and then try installing Beryl/XGL.

---

### Post by nicktrik on 2007-01-26
I have a Acer Aspire with UBUNTU edgy. Have managed after a lot of hard work to get Xgl and Beryl working.
The results are incredible. Totally forgot what Windows are.
Beryl is possible on the aspire series.

---

### Post by knlgSeekr on 2007-01-29
> **nicktrik said:**
> I have a Acer Aspire with UBUNTU edgy. Have managed after a lot of hard work to get Xgl and Beryl working.
The results are incredible. Totally forgot what Windows are.
Beryl is possible on the aspire series.

how did you do it? i was able to get my resolution to 1280x800 but have been unsuccessful with getting Beryl or 3ddesk to work with this chipset (SIS 760GX)

Acer Aspire 3004WLMi

---

### Post by nicktrik on 2007-02-05
Just followed the wiki at [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)

Must admit had a problem after updating the beryl drivers but then upgrated to beryl with svn source after a bit of googling and everything back to normal again

---

### Post by jay6 on 2007-04-02
I've been trying to install beryl and get it to work on my machine for months, every once in a while just saying "Well, might as well go at it again"...

Every time I've had to re-install ubuntu completely.

So, then I thought "well, hell, ultimate ubuntu 1.3 says it has beryl preinstalled, maybe that will just "magically" get it to work".

It crashes everytime you start it.

Now I find this thread, yay! 

> *from the wiki* There are lots of howtos for this , Google if you need any help with that. !
The person who wrote that must have been using a different google than I am, because every damn time I look for 3d acceleration, I well, end up needing to reinstall ubuntu because of tutorials that lead me nowhere.

If any of you kind, kind individuals could give me a better direction as to how to get this  beryl working, I'd be forever grateful.

I should also mention I have the acer aspire 5000 as well. Ubuntu edgy, 6.10 I would assume.

---

### Post by jay6 on 2007-04-23
Anyone?

---

### Post by lilBeat on 2007-12-17
To update this thread:

I have still the same laptop (see post #1), but Kiwi Linux 7.10 on it. Kiwi is modified Ubuntu 7.10. 

Many things changed about 3D this year in Linux world, but I still can not have it on my laptop. 

On Ubuntu 7.10 it is really easy to turn on/off 3D: System>Preferences>Appearance. On tab Visual Effects one can select None, Normal or Extra. If you select Normal and you have already by default selected None, and if your computer is not capable of running it, then it will reselect default None. That is what it is doing on my computer (at least).

So, hoping further development of 3D I am looking forward to see it running on this laptop.

---

