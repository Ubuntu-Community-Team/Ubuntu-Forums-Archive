---
title: "WLAN is freezing/making my computer unusable"
date: 2009-04-03
forum: General Help
---

### Post by Ecstatic23 on 2009-04-03
OK this is basically a reply to my other post: [http://ubuntuforums.org/showthread.php?t=1113805](http://ubuntuforums.org/showthread.php?t=1113805)

Basically my computer freezes after attempting to load something.

I uninstalled things like compiz and it had no effect so I went in to the BIOS and one by one disabled onboard features. I found that the computer ran normally on everything except WLAN.

What could be the problem?

---

### Post by Ecstatic23 on 2009-04-03
bump?

---

### Post by ariedry on 2009-04-03
> **Ecstatic23 said:**
> bump?
yea i guess its kind of bump lol

---

### Post by Ecstatic23 on 2009-04-03
> **ariedry said:**
> yea i guess its kind of bump lol

Thanks for the help ](*,)

---

### Post by paradigm2 on 2009-04-03
Hmmm.  Are you saying that when your onboard WLAN adapter is enabled you have problems?  Perhaps a general install issue with it.  Maybe try reinstalling the driver.  Does another driver (possibly generic) work with it?

---

### Post by Ecstatic23 on 2009-04-03
> **paradigm2 said:**
> Hmmm.  Are you saying that when your onboard WLAN adapter is enabled you have problems?  Perhaps a general install issue with it.  Maybe try reinstalling the driver.  Does another driver (possibly generic) work with it?

..I don't understand a word of what you typed..

I just went on my computer and it was like that.

---

### Post by paradigm2 on 2009-04-03
> **Ecstatic23 said:**
> ..I don't understand a word of what you typed..

I just went on my computer and it was like that.

Sorry about that...
WLAN stands for "Wireless Local Area Network".  It is your WIFI (internet wireless) card.  It sounds like when you disable that things are working.

But how are you getting to the internet now.  Is your wireless internet working on that computer right now?  Or are you connecting by a wire or a different computer?

A "Driver" is basically a piece of software that makes the hardware (your wireless adapter for example) work.  Often there are multiple possible drivers for one wireless card so if you have problems with one, the other might work.

To start us off in helping you can you go to Applications in the upper left hand corner, then "Accessories", then Click "terminal".  Now when that comes up type in "lspci" without the quotes.

A bunch of weird output like:

```

david@ubuntu-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
david@ubuntu-laptop:~$ 

```

Will come up.  Highlight it by going to the start of it and holding down the left mouse button.  With the left mouse button down move down with your mouse/touchpad to select more of it until the end.  Then hit with it highlighted click and the mouse pointer over the area you highlighted, please click the right mouse button once.  A menu will pop up.  Select copy.  Now post that into your post here on the forums by hitting right clicking here where you are typing and then choose paste.  This will help us see what you have as far as hardware on your system and it is called "cut and paste".  You'll probably be asked to cut and paste something many times. :)

---

### Post by Ecstatic23 on 2009-04-03
> **paradigm2 said:**
> Sorry about that...
WLAN stands for "Wireless Local Area Network".  It is your WIFI (internet wireless) card.  It sounds like when you disable that things are working.

I know that, I'm not completely useless =)

> But how are you getting to the internet now.  Is your wireless internet working on that computer right now?  Or are you connecting by a wire or a different computer?

I'm receiving wireless internet. It does work, after a lot of struggle, I managed to open FireStarter and bridge the internet to another computer.

A>  "Driver" is basically a piece of software that makes the hardware (your wireless adapter for example) work.  Often there are multiple possible drivers for one wireless card so if you have problems with one, the other might work.

To start us off in helping you can you go to Applications in the upper left hand corner, then "Accessories", then Click "terminal".  Now when that comes up type in "lspci" without the quotes.

A bunch of weird output like:

```

david@ubuntu-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
david@ubuntu-laptop:~$ 

```

Will come up.  Highlight it by going to the start of it and holding down the left mouse button.  With the left mouse button down move down with your mouse/touchpad to select more of it until the end.  Then hit with it highlighted click and the mouse pointer over the area you highlighted, please click the right mouse button once.  A menu will pop up.  Select copy.  Now post that into your post here on the forums by hitting right clicking here where you are typing and then choose paste.  This will help us see what you have as far as hardware on your system and it is called "cut and paste".  You'll probably be asked to cut and paste something many times. :)

I can't cut and paste, When I open firefox it just freezes up. That's how bad my problem is, If you can imagine Vista Premium running on a Pentium 1's performance, that's probably about the equivalent of my computers.

---

### Post by Ecstatic23 on 2009-04-03
Someone must know how to fix this...

---

### Post by Ecstatic23 on 2009-04-03
bump.

---

### Post by Ecstatic23 on 2009-04-03
Surely someone can help me!??

---

### Post by Ecstatic23 on 2009-04-03
............

---

### Post by CyberMando on 2009-04-03
Do you have both ethernet and wireless? If you do using them at the same time on the same subnet will can cause something like this.

---

### Post by Ecstatic23 on 2009-04-03
> **CyberMando said:**
> Do you have both ethernet and wireless? If you do using them at the same time on the same subnet will can cause something like this.

Even when I disabled LAN but not WLAN it does the same thing.

---

### Post by paradigm2 on 2009-04-03
> **Ecstatic23 said:**
> 

I can't cut and paste, When I open firefox it just freezes up. That's how bad my problem is, If you can imagine Vista Premium running on a Pentium 1's performance, that's probably about the equivalent of my computers.

Can you start it in single user mode or command line only (or if you can get to a terminal) and do

```

lspci > myconfigwithwlan

```

Then turn off your wlan adapter in the bios, reboot, and cut and paste from that file and post it here?  I think you said when you disable the wlan adapter in the bios all is fine....

We need to know what hardware you have in there.

---

### Post by Ecstatic23 on 2009-04-04
> **paradigm2 said:**
> Can you start it in single user mode or command line only (or if you can get to a terminal) and do

```

lspci > myconfigwithwlan

```

Then turn off your wlan adapter in the bios, reboot, and cut and paste from that file and post it here?  I think you said when you disable the wlan adapter in the bios all is fine....

We need to know what hardware you have in there.

Nothing shows up...?

It's an ASUS eee PC701 4G if that helps.

---

### Post by paradigm2 on 2009-04-04
> **Ecstatic23 said:**
> Nothing shows up...?

It's an ASUS eee PC701 4G if that helps.

Ok now we are getting somewhere. I did some research and found this:

[http://wiki.eeeuser.com/ubuntu#wireless_internet_using_native_madwifi_drivers](http://wiki.eeeuser.com/ubuntu#wireless_internet_using_native_madwifi_drivers)

Are you using ndiswrapper?

Also I found this: [http://code.google.com/p/eee-ubuntu-support/issues/detail?id=9](http://code.google.com/p/eee-ubuntu-support/issues/detail?id=9)

Anyway what instructions did you use to load Ubuntu and more specifically the WIFI on the eee pc?   What version of X/K/ubuntu did you put on there?

I'm thinking that it is a driver related issue.  When you disable your WIFI at the bios the drivers are nto getting loaded so it is working.  But when you try to load your wifi card Ubuntu tries to load it and it causes your PC to grind to a halt.  The good news is that if it is a driver config issue, it will be fixable.

---

### Post by Ecstatic23 on 2009-04-04
> **paradigm2 said:**
> Ok now we are getting somewhere. I did some research and found this:

[http://wiki.eeeuser.com/ubuntu#wireless_internet_using_native_madwifi_drivers](http://wiki.eeeuser.com/ubuntu#wireless_internet_using_native_madwifi_drivers)

Are you using ndiswrapper?

Also I found this: [http://code.google.com/p/eee-ubuntu-support/issues/detail?id=9](http://code.google.com/p/eee-ubuntu-support/issues/detail?id=9)

Anyway what instructions did you use to load Ubuntu and more specifically the WIFI on the eee pc?   What version of X/K/ubuntu did you put on there?

I'm thinking that it is a driver related issue.  When you disable your WIFI at the bios the drivers are nto getting loaded so it is working.  But when you try to load your wifi card Ubuntu tries to load it and it causes your PC to grind to a halt.  The good news is that if it is a driver config issue, it will be fixable.

First, thanks for the help so far. I've been a windows user all my life, until the last 6 months that is.

I have no idea if I'm using ndiswrapper, I've never heard of it before.

I'm using Ubuntu EEE which is basically Hardy which is modified to fit on the EEE pc's screen + one of those menus similar to the netbook remix one which I disabled.

I burnt the iso on to my usb and installed it on my eee PC's hard drive.

---

### Post by paradigm2 on 2009-04-04
> **Ecstatic23 said:**
> First, thanks for the help so far. I've been a windows user all my life, until the last 6 months that is.

I have no idea if I'm using ndiswrapper, I've never heard of it before.

I'm using Ubuntu EEE which is basically Hardy which is modified to fit on the EEE pc's screen + one of those menus similar to the netbook remix one which I disabled.

I burnt the iso on to my usb and installed it on my eee PC's hard drive.

You're welcome.  It can be hard at first but after everything is how you want it and installed it is easy again.

I've never installed on an eee before so hopefully someone else jumps in, btu if not I will try my best.

But where did you download the iso (if you know the http:// address that would be best) and di you use any instructions anywhere to do it?  Just so we can figure out what was done and see if that might have caused the problem.

---

### Post by Ecstatic23 on 2009-04-04
> **paradigm2 said:**
> You're welcome.  It can be hard at first but after everything is how you want it and installed it is easy again.

I've never installed on an eee before so hopefully someone else jumps in, btu if not I will try my best.

But where did you download the iso (if you know the http:// address that would be best) and di you use any instructions anywhere to do it?  Just so we can figure out what was done and see if that might have caused the problem.

I think this is it: [http://ubuntu-eee.tuxfamily.org/index.php5](http://ubuntu-eee.tuxfamily.org/index.php5) but they say the sites down because of lousy hosting.

I can't really remember how I installed it. It was basically the ubuntu CD, but on a USB. I just had it boot from the usb and install Ubuntu on the Hard drive.

I have had this running since October last year, so something recent must have stuffed it up...

---

### Post by paradigm2 on 2009-04-04
> **Ecstatic23 said:**
> I think this is it: [http://ubuntu-eee.tuxfamily.org/index.php5](http://ubuntu-eee.tuxfamily.org/index.php5) but they say the sites down because of lousy hosting.

I can't really remember how I installed it. It was basically the ubuntu CD, but on a USB. I just had it boot from the usb and install Ubuntu on the Hard drive.

I have had this running since October last year, so something recent must have stuffed it up...

Ok.. well here is that site as of January

[http://web.archive.org/web/20080103202508rn_1/ubuntu-eee.tuxfamily.org/index.php5?title=Main_Page](http://web.archive.org/web/20080103202508rn_1/ubuntu-eee.tuxfamily.org/index.php5?title=Main_Page)

Was it something like that?

That it used to work suggests different things then.  A common issue is that if you did use ndiswrapper, if the updater updated the kernel you typically have to reinstall your wifi drivers.  It'd be best if we can find those instructions and then redo them just for the wifi part.

Im out of my element here but if you can disable the WLAN (aka WIFI) and get normal functionality again, Id do that.  Then go into synaptic (System -> Administration -> Synaptic) and type in ndiswrapper under "quick search".  Is anything showing appearing with a green box by it?
If so, well probably need to mark those ... such as ndiswrapper-utils-1.9 and ndiswrapper-common... for complete removal and then reinstall and configure them later after you have renabled your WIFI driver.  *But don't do that yet.* (just tell us whether anything shows as being installed -- a green box y it) Wait a little bit until hopefully someone else who has more experience with an eee can come on and check this...

---

### Post by Ecstatic23 on 2009-04-04
> **paradigm2 said:**
> Ok.. well here is that site as of January

[http://web.archive.org/web/20080103202508rn_1/ubuntu-eee.tuxfamily.org/index.php5?title=Main_Page](http://web.archive.org/web/20080103202508rn_1/ubuntu-eee.tuxfamily.org/index.php5?title=Main_Page)

Was it something like that?

That it used to work suggests different things then.  A common issue is that if you did use ndiswrapper, if the updater updated the kernel you typically have to reinstall your wifi drivers.  It'd be best if we can find those instructions and then redo them just for the wifi part.

Im out of my element here but if you can disable the WLAN (aka WIFI) and get normal functionality again, Id do that.  Then go into synaptic (System -> Administration -> Synaptic) and type in ndiswrapper under "quick search".  Is anything showing appearing with a green box by it?
If so, well probably need to mark those ... such as ndiswrapper-utils-1.9 and ndiswrapper-common... for complete removal and then reinstall and configure them later after you have renabled your WIFI driver.  *But don't do that yet.* (just tell us whether anything shows as being installed -- a green box y it) Wait a little bit until hopefully someone else who has more experience with an eee can come on and check this...

No sign of ndiswrapper..

---

### Post by Ecstatic23 on 2009-04-07
....

---

