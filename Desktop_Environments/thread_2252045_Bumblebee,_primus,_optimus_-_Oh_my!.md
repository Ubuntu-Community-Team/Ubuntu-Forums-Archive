---
title: "Bumblebee, primus, optimus - Oh my!"
date: 2014-11-08
forum: Desktop Environments
---

### Post by jcllings on 2014-11-08
Entirely new to these but they sound awesome. I do have nVidia graphics
...how do I know if they will do me any good? My machine is a game box primarily targeting PlayOnLinux and StarCraft II.

---

### Post by grahammechanical on 2014-11-08
Does that machine have hybrid graphics? To put it another way, does the motherboard have a built in graphic adapter (usually by Intel)? And then do you also have a discrete graphic adapter that is slotted into an expansion slot?

If you do not have both but only one or the other you do not need Bumblebee or Primus. Besides, Primus is for Nvidia adapters when used with a built in video adapter. Nvidia calls that setup its Optimus technology. AMD/ATI have another method of hybrid graphics that Primus would not be suitable for.

If you clarify your hardware specification, I will resist the temptation to muddy the waters. :)

Will they do any good? Without them, you will wish that you had them. And I base that statement on the posts we had on this forum when Nvidia Optimus technology first came out and Nvidia refused for a long time to provide a Linux  Nvidia driver that made any kind of use of Optimus technolgy.

Regards.

---

### Post by jcllings on 2014-11-09
[http://www.asus.com/us/Motherboards/Z87DELUXE/](http://www.asus.com/us/Motherboards/Z87DELUXE/)

1st off it's an Asus Z87 Deluxe mobo as noted above with this nVidia card in it:

VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 640] 

and the MOBO has the following cut 'n paste directly from the manual:

Integrated Graphics Processor - Intel® HD Graphics support
Multi-GPU support Supports NVIDIA® Quad-GPU SLITM Technology (with 2 PCIe x16 
Multi-VGA output support: DisplayPort/Mini DisplayPort/HDMI port
Supports DisplayPort 1.2* with max. resolution of 4096 x 
2160 @24Hz / 3840 x 2160 @60Hz (for DisplayPort and Mini DisplayPort)
Supports HDMI with max. resolution of 4096 x 2160 @24Hz / 2560 x 1600 @60Hz
Supports Intel® InTruTM 3D, Intel® Quick Sync Video, Intel® Clear 
Video HD Technology, and Intel® InsiderTM
Supports up to three displays simultaneously
Maximum shared memory 1024MB

* DisplayPort 1.2 Multi-Stream Transport compliant; supports DisplayPort 1.2 monitor daisy-chain up to 3 displays graphics cards)

Supports AMD® 3-WAY/Quad-GPU CrossFireXTM Technology

---

### Post by lama2p0 on 2014-11-11
As mentioned before, the things you're talking about are for Hybrid Graphics, if you have a Desktop, you probably don't have Hybrid Graphics. You only need these things if you have Hybrid Graphics, without these, the default card will be used instead of the discrete card.

In my case, my laptop has Intel Graphics and GTX 870M, Hybrid Graphics, without Optimus or Bumblebee, the discrete card(GTX 870M) wouldn't be used, instead the Intel Graphics would be.

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

---

### Post by jcllings on 2014-11-11
Oh. Say that would be kool. I've a System76 laptop and that would be good because I can take it with me to [http://www.afktavern.com/](http://www.afktavern.com/) ;-) 
I tried getting it to run with POL before but no dice.  It's a great laptop, I just wasn't thinking "games" when I bought it.

---

