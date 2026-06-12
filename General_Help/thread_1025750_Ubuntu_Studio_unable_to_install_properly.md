---
title: "Ubuntu Studio unable to install properly"
date: 2008-12-30
forum: General Help
---

### Post by PamelaPopo on 2008-12-30
Hi, 

I've been trying to install Ubuntu Studio many times, and i can't seem to get it to work the way it should. 
I have a Dell Latitude D520, with an Intel Core 2 Duo chip. I have XP installed on one partition, and i would like to keep a dual boot.

I tried to install Ubuntu Studio 8.04 once, but it never worked. When i would boot in Ubuntu i would see the normal stuff while loading (the blue ubuntu sign and the white progression bar going through "Ubuntu Studio"). But then some weird stuff would happen, a sequence of different screens, either completely black or with white and coloured lines, and eventually my PC would freeze. 

So i tried to install 8.10 . Everything went fine, but the softwares didn't quite work the way they should. I have read somewhere that problems have been reported with Jack and other applications in 8.10 . There seems to be an issue with machines running a dual chip also, and i have read that one should not upgrade in this case. Also, it seemed like my soundcard wasn't working properly. I have an built-in mic on my laptop, plus the usual headphones/mic plugs. the problem is that the internal mic was working fine (i could record my voice using Audacity), but i couldn't record anything when plugging in another mic. 

This morning i have tried to reinstall 8.04. The installation went fine, and i have been able to log in and stuff. I downloaded all the updates that were recommended. I then restarted my laptop, and i saw that there were 2 different version of the kernel available in GRUB (one finishing with .19, and one with .22). The thing is that none of them is working now (i get the same weird lines when i start, and the PC freezes). 

I am not asking for much really. All i want to use in Ubuntu studio is Pure Data. As i want to use it live (by plugging an instrument into it), i need to have a very low latency (which i cannot achieve in XP with the performances of my laptop). So i don't really care if Jack and other softwares are not working perfectly, as long as my soundcard works fine with pure data. 

Could somebody help me out? I find it very frustrating to read all these things about people being very happy with Studio and no even being able to install it properly...

Thank you in advance!

---

### Post by PamelaPopo on 2009-01-01
Please! Can someone help me with that?

---

### Post by Mohamedzv2 on 2009-01-01
I believe that you'd be able to type in the terminal, "sudo apt get ubuntustudio-audio"

though I'm not completely sure. THat should get the sound programs like jack and any other programs related to music and sound

---

### Post by PamelaPopo on 2009-01-02
Do you mean typing this into the terminal of a plain ubuntu install? The thing is that really want to have the real time kernel of Studio 8.04, since my goal is to have the lowest latency possible...

---

### Post by Mohamedzv2 on 2009-01-02
Are you sure there is any difference between the two kernels other than the programs in the distro?

And also, I think it would work if you have Ubuntu Studio, so you should try it.

---

### Post by PamelaPopo on 2009-01-02
I'm not a 100% sure, but it seems like Ubuntu has the basic kernel whereas ubuntu studio's is real time ( -rt).
 

I'm thinking of using Pure:Dyne instead. It's a live OS designed specially for Pure Data, and it's optimized for audio. I hope i'll be luckier with this one...

Thanks for your help anyway!

---

### Post by PamelaPopo on 2009-01-03
:( 

Pure Dyne doesn't seem to work any better...

I think i might as well ask the guys on the Pure Data forums what would be the best solution for me...

It's getting very frustrating...

---

### Post by Bucky Ball on 2009-01-14
> **PamelaPopo said:**
> I'm not a 100% sure, but it seems like Ubuntu has the basic kernel whereas ubuntu studio's is real time ( -rt).

Correct. You need rt kernel. Remember: the rt kernel has major problems with the Nvidia restricted drivers. If you are running them, uninstall them or you won't get far. Having said that, if you are just plugging in one mic and recording a single stereo track that should be no worries on any kernel (rt or otherwise). See how far you can stretch it if you intend doing more.
 

> **PamelaPopo said:**
> I'm thinking of using Pure:Dyne instead. It's a live OS designed specially for Pure Data, and it's optimized for audio. I hope i'll be luckier with this one...


Pure Dyne was my next suggestion. It isn't *exactly* designed for Pure Data, you will find plenty of other interesting stuff there too.

One thing I will say is that unless you have a couple of hard drives in your laptop, one of them at least 7200 rpm, I wouldn't get too serious with your recording projects. You might try recording tracks until you crash the machine to work out your limit, but you probably won't get that far. You will notice when things start to get sluggish. If you intend on using effects etc, be wary. They take up resources aplenty. Also, got plenty of RAM? 

See what you can achieve on your box, but the real time kernel is best. You will get results without it, of course. You could always try straight ubuntu and load the studio packages into that (my DAW is Xubuntu for the Xfce desktop manager with the UStudio packages loaded and the rt kernel). 

```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```That will get 'em all. From this page:

[http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/](http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/)

It is for 7.10 but works fine (that is what I used in 8.04.1 but deleted 'ubuntustudio-desktop' from this command as I don't like the artwork much).

Incidentally, having the .22 and .19 kernels is normal. If you screw .22 beyond repair(!) you can use .19 to try and fix it or at least use the box.

Good luck with it all. :)

---

### Post by Sabayon on 2009-01-14
Hey I had a similar problem once.

---

### Post by PamelaPopo on 2009-01-18
Thank you Bucky Ball for your answer. To be honest i have given up for the moment. I tried Pure Dyne, and i have to admit that it's a pretty nice thing, and the fact that one can run it from a cd amazes me (it doesn't take much to put in a deep state of awe!). It's got all the apps that i could use too, including Hydrogen, which it really neat. The things is that my laptop is probably too weak and old for Pure Dyne to work fine. And i will not get rid of XP and it's partition, because this is the only (fairly recent) computer i have and i need it for work. So i guess i'll just wait until i buy another computer to seriously start looking to the linux side of the force. 
For now i'm using an external usb soundcard which enables me to get below 10 ms latency in XP, which is sort of fine given that i'm only experimenting with Pure Data at the moment. 
I'm sorry, but i have to confess that i'm more interested in playing and recording music than with Ubuntu in itself...

Thanks again for your answer though!

---

### Post by Bucky Ball on 2009-01-18
My pleasure. Know what you are saying. I have a desktop DAW dual booting XP with Cubase, Protools, Reason Adapted, Sibelius etc etc. All the things you'd expect for that environment. There are others you might like to check; Spear, Plogue Bidule (if you're into PD, you might like this a lot). Did music tech at uni last year and used lots of bits and pieces, a lot I forget now.

The other boot on that machine is Xubuntu with Ubuntu Studio desktop and the low latency rt kernel, without the desktop (artwork) if you follow me. Still experimenting but so far working a treat.

Good luck with it all and if you post any music on the net anywhere, PM me. :)

ps: yea, hydrogen is fun! \\:D/

---

### Post by LeftHandThread on 2009-02-09
I too wanted to have both the real-time kernel (x86_64 aka 64 bit) and the restricted NVidia drivers on the same system and I don't see why that cannot be the case.

My system is somewhat long-in-the-tooth but not that bad:

* AMD Dual Core Athlon-64 2.4GHz (4200+)
* VIA motherboard with 5.1 sound support (Linux supported)
* 2GB DDR-400 memory
* NVidia 7300 GS (PCI-E)
* 500GB SATA-2 hard disk

I had a fully working system under 8.04 (generic kernel) but decided that I wanted:

* Ubuntu 8.10
* Real-time kernel (to use [Rosegarden]("http://www.rosegardenmusic.com/"), Hydrogen, Ardour etc)
* Still have development software e.g. Code::Blocks, Lazarus, Eclipse etc

so I upgraded to 8.10 and didn't check the small print.  
Bad move!  
SMP not supported under 2.6.28 kernel with real-time patches (what!)

Started from scratch again - installed:

* Unbuntu 8.04-2 (x86_64) with generic kernel
* Saved xorg.conf when I got it working.
* UNINSTALLED restricted drivers (+ reboot)
* Installed realtime kernel + restricted modules + backports (+ rebooted as RT)
* Installed nvidia-glx (NOT nvidia-glx-new)
* Replaced xorg.conf (with NV) with saved xorg.conf (nvidia) (+ reboot)
* Voila! Realtime kernel working with (slightly older) NVidia drivers :)

Now installed ubuntustudio-desktop and we have a fully working Ubuntu Studio system with a real-time kernel + 3D NVidia support.

This is as close to Nirvana as I wanted.  Everything seems to work fine (including VirtualBox 2.1, I have a low latency system with the benefits of being able to use real-time applications but can also use everything else as well.  I have also done this hack on my children's PC which is running [Edubuntu]("http://www.edubuntu.org") 8.04 (x86_64).  When I am brave enough, I will hack my MythTV box (which is also running 8.04 and has an NVidia card) and get the pre-emptive kernel running on there as well.

Ubuntu 8.04 or 8.10 with a real-time kernel and FGLRX drivers - just forget it!  I tried hard to get my old ATI X600 card (which is supported by the version of FGLRX in 8.04) running with the real-time kernel but to no avail.

I would LOVE to be running 8.10 but cannot do this without using the NVidia installer + hacking the source code before compiling the kernel objects.  Not trivial (and I have written *simple* kernel drivers) and frankly impossible for non-technical users.

This makes me think that:

1) The preempt RT kernel should be the default desktop kernel.  What reason is there NOT to have a pre-emptive kernel on a desktop system!

2) The RT kernel works (i.e. no glaring omissions like no SMP with real-time on the 8.10 kernel!)

3) All graphics drivers (including NVidia/FGLRX) which are in the Ubuntu repositories should just work with all kernels (real-time or otherwise)

Yeah I know that the long term aims should be to move to the open source ATI/AMD driver and Nouveau (open source NVidia driver) but the guys are working flat-out on these and they won't be ready in time for 9.04 (see [Phoronix]("http://www.phoronix.com/scan.php?page=home") for details).  For now the closed source drivers have to do.

The main thing is that we can get disgruntled Microsoft Vista users (and there are a lot of these including my wife) to move over to Ubuntu and for that to happen the quality control has to be very good.

Like many Ubuntu users I am quite prepared to help in any way that I can so am not afraid of hard work in supporting my favorite distro :)

---

