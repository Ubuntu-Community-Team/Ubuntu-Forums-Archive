---
title: "Gaming &amp; the ATI open source driver"
date: 2009-10-17
forum: Gaming &amp; Leisure
---

### Post by cisforcojo on 2009-10-17
I have an ATI Mobility Radeon X600 card which is no longer supported by ATI's catalyst driver. Although the performance for the open source driver is already very impressive, this has nearly destroyed my gaming options under Linux. 

Does anyone know where I can find the last version of ATI catalyst that supported my card or have any other solutions for me?

Even Privateer: ASCII Sector is choppy! (It's not really a true ASCII game)

Some games I play are:
X2 - The Threat
Savage
TeeWorlds
Warsow
Nexuiz
pSX (PS1 game emulation)

Thanks for any suggestions you might have to solve this issue. :)

---

### Post by benmoran on 2009-10-18
You have to go back to using Hardy or Intrepid if you want to use Catalyst. First, you should try the Xorg Edgers ppa. It has fairly recent builds of the free drivers. I'm running that.

---

### Post by Lodamned on 2009-10-18
Hi, you can try using catalyst 9.3:) after that catalyst they dropped support for all pre HD cards.

Check this link:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.19&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.19&lang=English)

---

### Post by iheartubuntu on 2009-10-18
From my experience, after Ubuntu 8.04 you are screwed. I never could get catalyst 9.3 to work... in fact it would screw up my system after trying to install it.

If you are that much into gaming, Id pay the $50-$70 and a get a no name nVidia 500mb video card. Try pricewatch.com for the best prices. You'll need to know what kind of video slot you have...PCI, PCI-Express, etc. 

otherwise, if you have a laptop and cant change the video card the only option I have gotten to work is using Ubuntu 8.04 and loading the EnvyNG ati drivers for the easiest driver installation. Go here to install the EnvyNG ati drivers... [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

If you have a newer version of Ubuntu already installed, maybe you can do a dual boot Ubuntu 9.10 and 8.04 just so you can run your games?

---

### Post by oldrocker99 on 2009-10-18
I'm running Intrepid with the 9.03 drivers and most everything works just fine. I'm going to resurrect my old desktop with an nVidia card for 9.10 so I can play some games that won't run in my laptop's measly 128 MB of video RAM.

Intrepid has treated me pretty well over the last year. I tried Jaunty with the open-source drivers, and liked it, but I'm too much of a Neverwinter Nights fan to be able to put up with the poor performance those drivers gave me. I still don't know if Karmic will do for ATI users what they have announced for Intel users. Does anybody know?

:guitar:

---

### Post by handy on 2009-10-20
Some of the links at the bottom of the [**_first post in this thread_**]("http://ubuntuforums.org/showthread.php?t=1238129") may be helpful.

There are changes incorporated into the .31 kernel which will effect some of the ATi GPUs; the .32 kernel will continue, incorporating changes that will benefit other ATi GPUs.

The open-source driver situation for ATi GPUs is changing pretty quickly, thankfully.

---

