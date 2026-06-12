---
title: "Tough Technical Hardware Problem"
date: 2006-09-04
forum: Debian
---

### Post by Mrbigshot08 on 2006-09-04
Hi, I decided to switch from Dapper Drake to Debian Etch Kernel 2.6.16 about a month ago on my Desktop, and am happy to say, I love it, and have done well, except for one small problem.

I have a serious problem when booting up my computer. It simply will not boot up. It starts booting the Kernel, then it gets to PnP ACPI detection and then it freezes on "Pnp:00:02: ioport range 0xe400-0xe47f could not be reserved". Then it prints out a few more similar Pnp lines and then the computer just freezes. Usually, I unplug the computer and try again, and eventually after a few tries or so, it will actually continue to boot normally. I had a similar problem with Ubuntu Breezy Badger when I was using that, but Breezy didn't print out all the information when it was booting the Kernel, it would just plain freeze. Dapper Drake seemed to fix the problem with one of the Kernel updates.

I have done some research on my computer and on the web and it appears the problem is my ethernet card. (Although I am not 100% sure). Apparently it is trying to use the ACPI to communicate but it can't. I have read that certain computers that were made for Windows that use ACPI, malfunction because they do not use official ACPI standards and therefore are incompatible with Linux but work fine on Windows because Windows knows this non-standard code. (This may or may not be the problem, I can't be sure).

One of the things that has led me to believe that the problem is my onboard ethernet card is that during the times when I do manage to get the computer to boot, I get the following error, "eth1 unknown hardware address type 24" 

I have made some efforts to get this resolved but have failed. I tried installing the non-pci ethernet card tools and extra ACPI support packages, both obviously were not going to work, I don't know why I even bothered.](*,) Luckily, I do not rely on this ethernet card for anything, I do not use it at all, nor do I plan to use it. I have a PCI Wireless adapter that I use for my internet needs.

Basically any information to help solve this problem would be appreciated.  Since I don't use this ethernet card, I think disabling completely would be one valid solution, but I don't know if that is even possible. Basically this isn't a bad problem, but I would like to know what it is and find any kind of solution, since it is kind of annoying when you want to turn on your computer, but have to try about five times. (Yes, I know, I could simply leave my computer on all the time, and I have been doing that more, but I would like to have the luxury to allow my computer to rest occaisonally, as I have already blown one power supply this year).

Sorry for the long post, but I felt like I needed to explain my problem as best as I could.

And now the part you have all been waiting for... The system information! This is a desktop computer that I pretty much pieced together from random parts. It used to be a Sony Vaio, but now it has some of my own additions,  but the parts that matter are still Sony Vaio parts, any way here we go.

Kernel 2.6.16-2-686
1.5 Ghz Intel Pentium IV
I don't know exactly what the motherboard is but the computer is a Sony Vaio PCV-RX550
Graphics: NVidia 4x AGP TNT2 M64
Ethernet: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
Intel Corporation 82801BA/BAM AC'97 Audio
RaLink RT2500 802.11g Cardbus/mini-PCI (not onboard obviously)

If there is any other information you want, don't be afraid to ask, just tell me the exact command. I guess I should have just posted lspci, but Thanks in advance, I'll stop writing now.

---

### Post by Rumor on 2006-09-06
You might want to post this in the Debian forums too to see if anyone there has a suggestion. I tried searching there using some of the keywords in your problem description, but I don't think I was finding answers that fit your exact situation.

[http://forums.debian.net/index.php](http://forums.debian.net/index.php)

---

### Post by tturrisi on 2006-09-06
To determine if the issue is caused by the onboard nic then boot to the bios & disable the onboard nic.  The bios will have a section where you can enable-disable onboard devices. If still get same error then the nic has nothing to do w/ the problem.

I use etch on my laptop and I use kernel 2.6.15-1-686 SMP because the cpu is a 3.02ghz w/ hyperthreading.

---

