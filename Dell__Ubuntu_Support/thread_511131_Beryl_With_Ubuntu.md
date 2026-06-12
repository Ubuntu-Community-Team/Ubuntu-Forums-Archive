---
title: "Beryl With Ubuntu??"
date: 2007-07-27
forum: Dell  Ubuntu Support
---

### Post by scorpiox on 2007-07-27
I tried to get onto the Beryl forum but it wont let me register, so ill post here and hope for the best

I installed Ubuntu 7.04 last night, and i love it. I replaced Windows completely, and i am having a great time.

I then tried Beryl, and no matter what i try, i cant make the effects work. Does anyone have any ideas? I tried enabling desktop effects, which are the wobbly windows and cube, but teh cube stopped working after not that long, and the wobbly windows arent Beryl i dont think, im pretty sure its just Ubuntu.

Can anyone help me get it working, so i can use Beryl properlly? I also tried the wiki for beryl ,but it is closed. Im relatively new to Linux , so any suggestions would be greatly appreciated.

Also, whether or not wobbly windows is enabled in Beryl, if its enabled in desktop effects (preferences), it works. If its disabled there, then it doesnt work. Beryl doesnt appear to be affecting it at all. 


I have A dell Inspiron 1150 with 1280mb RAM and a 2.4ghz processor, in case it matters.

Look forward to making it work :)

~G~

---

### Post by rombel4u on 2007-07-27
what is the amount of video ram you have. if you have less than 128MB of video ram like me  then beryl wouldnt work. i think there is some memory management issue for video card with memory less than 128MB.

---

### Post by scorpiox on 2007-07-27
That would make sense. Is there a way to make other little bits on it work? I have shared memory on it, and it leeches off the RAM, i think.

---

### Post by timcredible on 2007-07-27
you need a 3d graphics card for beryl to run.  nvidia is easier than ati.  you can buy an older nvidia card for about $20 on ebay that will work (i paid $24 for my nvidia 4000 a couple years ago and it works with beryl, although not as fast as i would like).

---

### Post by Rocket2DMn on 2007-07-27
> **rombel4u said:**
> what is the amount of video ram you have. if you have less than 128MB of video ram like me  then beryl wouldnt work. i think there is some memory management issue for video card with memory less than 128MB.

I run Beryl on a 64MB ATI Radeon Mobility 9000.

---

### Post by scorpiox on 2007-07-28
> **Rocket2DMn said:**
> I run Beryl on a 64MB ATI Radeon Mobility 9000.
Cousin is running it on a laptop identical to mine, although mine has about 1 and a half times as much RAM, but its only mine that doesnt work. The cube doesnt work for him, but everything else does. However, on mine, nothing works, i cant make anything happen.

~George~

---

### Post by Rocket2DMn on 2007-07-28
What type/model video card do you have?  Sounds like it might be a driver issue.
Please also post the output of
```
lspci
```

---

### Post by scorpiox on 2007-07-28
Its just the built in Intel Chip that comes with the laptop, im not sure what exactly.

Output:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

---

### Post by Rocket2DMn on 2007-07-28
Here is a very basic guide to setting up Beryl, try the directions for intel: [http://doc.gwos.org/index.php/BerylOnFeisty](http://doc.gwos.org/index.php/BerylOnFeisty)

There are also other threads on setting up Beryl using an intel card, you can search around and pick up pieces.  I think people tend to generally recommend the generic i855 drivers rather than compiling intel's drivers from their site.
All the extra effects might now work because of the limited capacity of your video card.

---

### Post by DerangedDingo on 2007-07-29
Wait a second, I have I think.. the same video card. It's a 64mb Intel Graphics Controller, and I use Compiz all the time.

I think you just had some trouble setting it up.
There should be guides on line for Intel cards

---

### Post by scorpiox on 2007-07-29
I installed via synaptic, if i get rid of it completely via that, i can start again, and tehn follow any intel guidlines, right?

THANKS!

---

### Post by Junkhead on 2007-07-29
My suggestion is to use Compiz-fusion instead of Beryl.

Here's a link to instructions on how to use it:

[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

Compiz Fusion is actually pretty stable and usable, despite what that forum post says.
Just follow the instructions (it's alot easier than it looks) and before you know it, you'll have 3D effects
on your desktop.

Also, ensure that your graphics drivers are properly installed and are in use, since that can cause problems.

---

