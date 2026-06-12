---
title: "Building A Gaming PC With Ubuntu In Mind"
date: 2013-12-08
forum: Gaming &amp; Leisure
---

### Post by paul.Michael.peter on 2013-12-08
Hello Ubuntu Forums,

I have been an Ubuntu user since the Feisty Fawn days of old.  I have enjoyed my time with Ubuntu.  I have also been a gamer but I had been exclusively console so I never needed to worry about games on Ubuntu/wine.  However, that all changes this generation.

I'm looking to build a gaming PC that matches or surpasses the XB1 and PS4.  I have settled on the following

CPU: AMD FX 6300
GPU: AMD HD 7850 or 7870 (depending on price)
Mem: 8 GB

I'll be using my PS3 controller

Before I start buying parts I am looking for some help.  Are there any issues with playing games on Ubuntu?  Does Nvidia work better than AMD or vis versa?  Anyone who has already gone down this road have any tips and tricks? 

I'm expecting to play the latest games right off the bat. (I'll be testing this rig with Battlefield 4, The Wicher 2, GTA V and Watch Dogs.) I also want to continue playing new releases for a few years as well. I understand the specs are middle of the road but this just need a to replace a PS4 not blow it away.

Any and all help is appreciated. I don't want to spend this kind of money and then have to start using Microsoft Windows again.  I'm sure you can understand. ;)

Edit:

Never mind about Battlefield 4.  Turns out that won't be happening

---

### Post by oldrocker99 on 2013-12-08
This is something you hear a lot on Linux forums, and I'll state it Yet Again: Linux gamers are at present far happier with nVidia cards and their proprietary drivers than they are with ATI and its drivers. Currently Painkiller: Hell and Damnation's forums, in beta for Linux on Steam, are rife with complaints from ATI owners about how they can't get the game to run. It runs like a top on my AMD 965 with nVidia GeForce 650ti, 3.19 drivers. nVidia is also working pretty hard to improve their Linux drivers, in other words to get them in parity with their Windows drivers. ATI is also working on their drivers, but the sad truth is that ATI abandons their "legacy" cards and chips, and stops making drivers for them, while a five year old nVidia card can run the newest drivers. 

Also, I can play both Witchers, Skyrim and Oblivion on Ubuntu using PlayOnLinux, a wrapper for wine, which is the program that lets *nix systems run **some** Windows programs. They all run quite well. I do dual-boot for those games that won't run under wine (and there are a lot), but, in the last year, I've booted into Windows less and less often because the games I play most often are available for Linux, mostly from Steam for Linux and also Desura. And I can still play the Elder Scrolls and Witcher games. Best o' both worlds.

---

### Post by paul.Michael.peter on 2013-12-08
Thanks for the tip on Nvida.  My choice of ATI isn't set in stone and if headaches await me with ATI I'll leave it before I arrive.  

I was hoping to avoid dual booting into windows at all but from what you said and the word on the web in general, that isn't realistic if I'm to enjoy all the games I want to.

Thank you again.

---

### Post by DanglingPointer on 2013-12-09
Yeah mate, linux gaming is good but it isn't "great" yet. 
 I would say perhaps by the second half of next year when SteamMachines/SteamOS is in full swing and hopefully AMD have gotten their act together with their drivers.

IF:
[LIST]
[*]You want to build your own SteamMachine console or Ubuntu-with-Steam console
[*]Want it more powerful at roughly the same price or cheaper than the new consoles
[*]You want similar number of game engine optimisations and draw calls as consoles (games running direct to metal like the PS4 and XBONE)
[/LIST]

I would wait till Kaveri is out then get a 270X next year.
It will be cheaper than the consoles or roughly the same price 
AND 
It will be more powerful than all consoles
AND
For many blockbuster AAA games ported from consoles to PC, they are likely to use Mantle thus will be optimised for AMD-GCN with similar number of draw calls
PLUS BONUS
AFR capability (Asymmetric Frame Rendering; in other words, crossfire any Kaveri-APU[or newer] with any AMD-GCN dGPU).

---

### Post by MikeCyber on 2013-12-10
Very happy with my new pc as below even my webcam is now working perfectly with guvcview. Pan, zoom etc. all fine in Ubuntu 13.04. But not in Windows 8 anymore.

[LIST]
[*]                                                      Processor:[COLOR=red]**Intel Core i7 4770K**[/COLOR] 
[*]**                                                      Processor Cores:4                                              ** 
[*]**                                                      Processor Speed:ovc to 4.6 Ghz                                              ** 
[*]**                                                      RAM:16 GB (Corsair Vengeance Pro Red 2x 8GB, DDR3-2400)                                              ** 
[*]**                                                      Video Board Manufacturer:Nvidia                                              ** 
[*]**                                                      Video Board Model:Asus GTX-770 DirectCU II 2GB GDDR5                                              ** 
[*]**                                                      Video Memory:2 GB                                              ** 
[*]**                                                      Mother Board:Asus Z87 PRO                                              ** 
[*]**                                                      Hard Drives:Samsung SSD 840 Basic, TLC, 500GB and 1TB HD                                              ** 
[*]**                                                      Monitor:LG L225WT                                              ** 
[*]**                                                      Operating System:Ubuntu etc.                                              ** 
[*]**                                                      Joystick:CH                                              ** 
[*]**                                                      Yoke:CH                                              ** 
[*]**                                                      Rudder Pedals:CH                                              ** 
[*][B]                                                      Other:Corsair H90
 Asus DVD Burner
 Logitech cordless usb MK260 and QuickCam® Sphere™                                              [/B] 
[/LIST]

---

### Post by oldrocker99 on 2013-12-10
It's kind of a (or it should be) no-brainer to dump the execrable Windows 8 and go to GNU/Linux. I just feel sorry for the folks (inclusing relatives and friends) who feel so wedded to Microsoft that they won't even consider a far superior OS.

---

### Post by Arthur_D on 2013-12-11
For your purposes I also recommend NVIDIA as the best choice right now. AMD may become just as good or even better in a year but I wouldn't count on it really.

For people not doing a lot of gaming, i.e. medium games AMD is probably fine (and maybe even better as you aren't required to install proprietary drivers). But if you push the card NVIDIA tends to have better performance and stability.

---

### Post by King Dude on 2013-12-12
Have you considered using the SteamOS? I mean, we all love Ubuntu, but SteamOS would probably be better for gaming, and you could dual boot Ubuntu on another drive.

> **Arthur_D said:**
> For your purposes I also recommend NVIDIA as the best choice right now. AMD may become just as good or even better in a year but I wouldn't count on it really.

For people not doing a lot of gaming, i.e. medium games AMD is probably fine (and maybe even better as you aren't required to install proprietary drivers). But if you push the card NVIDIA tends to have better performance and stability.
I suppose it depends on what kind of CPU he acquires. If it is a standard CPU (AMD/Intel), then an Nvidia GPU may be better. However, if the OP decides to get an AMD APU (which quite frankly is my choice for power at a reasonable price), then he should get an AMD GPU as well.

Of course, AMD would have to update their drivers, and that would be happening sometime in 2014 when the SteamOS finally rolls out.

> **oldrocker99 said:**
> It's kind of a (or it should be) no-brainer to dump the execrable Windows 8 and go to GNU/Linux. I just feel sorry for the folks (inclusing relatives and friends) who feel so wedded to Microsoft that they won't even consider a far superior OS.
It's hard to break the habit when they have been institutionalized on Windows for the past twenty or so years.

---

### Post by Dlambert on 2013-12-12
SteamOS beta/alpha images will be launching tomorrow, so I'd definitely try that out. +1 to Nvidia, although I'm buying a 290X soon.

---

### Post by oldrocker99 on 2013-12-13
To King Dude:

OK, I started out with a VIC-20 in 1983, then a Commodore 64 in 1984, then an Amiga in 1986, which I used (and loved; its OS was based on UNIX) until 1996, when I got a Windows 3.1 PC as a Xmas present, then went to Win95 (hated), Win98 (liked), WinME (HATED), XP (liked, until the 98237347675th virus attack, when I said, "fuggedaboutit" and wiped out that pig pile of bleeding security holes with Ubuntu 8.04, and have barely looked back since. I do dual-boot with Win7, for one purpose only: to play games (IMHO, the one and only thing Windows is good for). In the last year, I've been booting into Windows a whole lot less often.

I know some people are joined at the hip with Windows, but Microsoft, once Ruler Of The Waves, is now docked and rapidly taking on water. It's a big damned ship, but it will sink sooner or later.

Tonight I got email from Microsoft with their tone-deaf "Scroogled" campaign. I told them what they could do with their campaign, and pointed out that I was using Linux on a Chromebook, and my wife (a computerphobic person just this side of being a Luddite) LOVES her Chromebook. So there.

---

### Post by dannyboy79 on 2013-12-14
> **King Dude said:**
> . However, if the OP decides to get an AMD APU (which quite frankly is my choice for power at a reasonable price), then he should get an AMD GPU as well.

just because someone has an AMD CPU does not mean they need to run an AMD/ATI/RADEON Graphics Card. just had to post my 2 cents on that.  I currently am running an XFX HD7770 Black Edition (I run the latest BETA AMD Driver, 13.11 V9.4) and the only game I can't play due to running fglrx is Painkiller Hell and Damnation because of some graphics bug but it runs fine with either Nvidia drivers or the open source AMD driver. So at this very point in time I am very satisfied with my Radeon GPU but whenever I advise others about what hardware to get I will always say Nvidia and even more so now due to Nvidia and Valve working so closely on SteamOS together.

---

### Post by oldrocker99 on 2013-12-14
> **dannyboy79 said:**
> just because someone has an AMD CPU does not mean they need to run an AMD/ATI/RADEON Graphics Card. just had to post my 2 cents on that.  I currently am running an XFX HD7770 Black Edition (I run the latest BETA AMD Driver, 13.11 V9.4) and the only game I can't play due to running fglrx is Painkiller Hell and Damnation because of some graphics bug but it runs fine with either Nvidia drivers or the open source AMD driver. So at this very point in time I am very satisfied with my Radeon GPU but whenever I advise others about what hardware to get I will always say Nvidia and even more so now due to Nvidia and Valve working so closely on SteamOS together.

Well put!

---

### Post by King Dude on 2013-12-16
> **dannyboy79 said:**
> just because someone has an AMD CPU does not mean they need to run an AMD/ATI/RADEON Graphics Card. just had to post my 2 cents on that.  I currently am running an XFX HD7770 Black Edition (I run the latest BETA AMD Driver, 13.11 V9.4) and the only game I can't play due to running fglrx is Painkiller Hell and Damnation because of some graphics bug but it runs fine with either Nvidia drivers or the open source AMD driver. So at this very point in time I am very satisfied with my Radeon GPU but whenever I advise others about what hardware to get I will always say Nvidia and even more so now due to Nvidia and Valve working so closely on SteamOS together.
Forgive me, but I'm afraid you may have overlooked the part where I mentioned "AMD **APU**". If you get an APU, the APU and the GPU can work together for extra graphics processing power, but *only if it is an AMD GPU*&#8203;.

---

### Post by paul.Michael.peter on 2013-12-16
Wow thanks for the help everyone.  Since my last post I was thinking about the Nvidia GTX 660 (no TI) due the longer support and easier use with linux.  However if the benefits are good enough to warrent me sticking with AMD gpu, I certainly will.  

When it comes to motherboards, I was seeing some okay ones at the $50 range. They do lack USB 3 and mist only have one PCI express card slot.

Should I even with about the USB 3 though? 3.1 seems right around the corner and I feel that getting a cheap one now and buying a good one later would make sense.

Thoughts?

---

### Post by King Dude on 2013-12-16
> **paul.Michael.peter said:**
> Wow thanks for the help everyone.  Since my last post I was thinking about the Nvidia GTX 660 (no TI) due the longer support and easier use with linux.  However if the benefits are good enough to warrent me sticking with AMD gpu, I certainly will.  

When it comes to motherboards, I was seeing some okay ones at the $50 range. They do lack USB 3 and mist only have one PCI express card slot.

Should I even with about the USB 3 though? 3.1 seems right around the corner and I feel that getting a cheap one now and buying a good one later would make sense.

Thoughts?
You want a motherboard with as much upgrade slots as possible. Think of it this way: If you were to buy a $50 motherboard over a $100-200 motherboard, it may be inexpensive right now, but with only one PCIe port you can only have one GPU, and your machine would be out dated in five years or less forcing you to spend another $500 or so on a new rig. However, if you spring for the more expensive board with multiple PCIe ports, you can add GPUs or other hardware as time goes on, making your machine capable of lasting ten or more years maybe with steady financial input.

If there is one perk to PC that is extremely important, it is **upgrade ability**&#8203;. You shouldn't cheat yourself out of that.

Also, new Nvidia video cards are going to have something called [G-Sync]("http://www.geforce.com/hardware/technology/g-sync") (designed to replace V-Sync). However, you'll need a G-Sync compatible monitor as well.

---

### Post by Dlambert on 2013-12-17
I still say you'd be happier with an Nvidia card. Honestly. 

But who knows, AMD'd drivers have picked up lately.

---

