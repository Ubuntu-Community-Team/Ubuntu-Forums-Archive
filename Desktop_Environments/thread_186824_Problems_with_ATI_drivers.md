---
title: "Problems with ATI drivers"
date: 2006-06-02
forum: Desktop Environments
---

### Post by simone.brunozzi on 2006-06-02
Hi there,
I just installed Kubuntu 6.06 dapper drake on my Sager 4760 laptop (1440x900 resolution, ati radeon 9600).
I have a problem with the graphic drivers... here it comes:

With X.org graphic drivers I wasn't able to stay at 1440x900; therefore, I tried to follow the instructions here:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

```
sudo apt-get update
sudo apt-get install linux-restricted-modules-2.6.15-23-386
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

And then ended up with a working 1440x900 resolution; however, if I run the command fglrxinfo, I get:

```
root@solaria:~# fglrxinfo
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: unable to open display :0

```

If I run the command dmesg | grep fglrx, I get:

```
root@solaria:~# dmesg | grep fglrx
[4294736.247000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294736.250000] [fglrx] Maximum main memory to use for locked dma buffers: 927 MBytes.
[4294736.250000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294737.694000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294737.694000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294737.694000] [fglrx] AGP detected, AgpState   = 0x1f004e19 (hardware caps of chipset)
[4294737.706000] [fglrx] AGP enabled,  AgpCommand = 0x1f004311 (selected caps)
[4294737.715000] [fglrx] total      GART = 67108864
[4294737.715000] [fglrx] free       GART = 51113984
[4294737.715000] [fglrx] max single GART = 51113984
[4294737.715000] [fglrx] total      LFB  = 126791680
[4294737.715000] [fglrx] free       LFB  = 116002816
[4294737.715000] [fglrx] max single LFB  = 116002816
[4294737.715000] [fglrx] total      Inv  = 0
[4294737.715000] [fglrx] free       Inv  = 0
[4294737.716000] [fglrx] max single Inv  = 0
[4294737.716000] [fglrx] total      TIM  = 0
```

Now, I need help in fixing this... any suggestions?

Thanks a lot!

Cheers,

---

### Post by Rackerz on 2006-06-02
Are you sure the fglrx driver is being used? When I run sudo aticonfig --initial it doesn't change it to fglrx as it should, I have to edit it myself in xorg.conf.

---

### Post by simone.brunozzi on 2006-06-02
Rackerz,
can you provide me details on how to correctly edit xorg.conf?
Are the instruction on the page I indicated on the top correct?

Thanks!



[QUOTE=Rackerz]Are you sure the fglrx driver is being used? When I run sudo aticonfig --initial it doesn't change it to fglrx as it should, I have to edit it myself in xorg.conf.[/QUOTE]

---

### Post by Rackerz on 2006-06-02
Ok first you will need open up your xorg.conf, do this by opening a terminal and typing;
```
sudo gedit /etc/X11/xorg.conf
```

Then you need to go to this line in the file;
> Section "Device"
Under that line you will see 'Driver "ati"' change it to;
```
fglrx
```
Then reboot.

---

### Post by simone.brunozzi on 2006-06-02
Hi again,
that line in the config file is correct. However, I still got the same problem.

Any hints?

Cheers,

---

### Post by Fry-kun on 2006-06-11
Hi,
same problem here, though different setup.
Everything worked in Breezy (at that time I used some guide to get the ATI drivers installed)

my setup:

arch: AMD64
OS: Breezy ---dist-upgrade---> Dapper
Vcard: 3DConnect X800 GTO
dual head setup (CRT + DVI)
main monitor (DVI) 1440x900

dmesg | grep fglrx:
```

[   74.850012] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   74.851808] [fglrx] Maximum main memory to use for locked dma buffers: 1884 MBytes.
[   74.851946] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[   76.632328] [fglrx] total      GART = 67108864
[   76.632349] [fglrx] free       GART = 51118080
[   76.632352] [fglrx] max single GART = 51118080
[   76.632375] [fglrx] total      LFB  = 126726144
[   76.632386] [fglrx] free       LFB  = 115937280
[   76.632628] [fglrx] max single LFB  = 115937280
[   76.632707] [fglrx] total      Inv  = 134217728
[   76.632781] [fglrx] free       Inv  = 134217728
[   76.632820] [fglrx] max single Inv  = 134217728
[   76.632833] [fglrx] total      TIM  = 0
[   76.754726] [fglrx] total      GART = 67108864
[   76.754762] [fglrx] free       GART = 51118080
[   76.754772] [fglrx] max single GART = 51118080
[   76.754900] [fglrx] total      LFB  = 126726144
[   76.754919] [fglrx] free       LFB  = 104382464
[   76.755036] [fglrx] max single LFB  = 104382464
[   76.755055] [fglrx] total      Inv  = 134217728
[   76.755079] [fglrx] free       Inv  = 134217728
[   76.755129] [fglrx] max single Inv  = 134217728
[   76.755159] [fglrx] total      TIM  = 0

```

lspci -vv:
```

0000:01:06.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27) (prog-if 00 [VGA])
        Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 66 (2000ns min), Cache Line Size: 0x10 (64 bytes)
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at b1000000 (32-bit, non-prefetchable) [disabled] [size=16M]
        Region 1: I/O ports at 2000 [disabled] [size=256]
        Region 2: Memory at b0100000 (32-bit, non-prefetchable) [disabled] [size=4K]
        Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: [5c] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:03:00.0 VGA compatible controller: ATI Technologies Inc R423 UI [Radeon X800PRO (PCIE)] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc: Unknown device 0312
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 0x10 (64 bytes)
        Interrupt: pin A routed to IRQ 50
        Region 0: Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Region 2: Memory at b2000000 (64-bit, non-prefetchable) [size=64K]
        Region 4: I/O ports at 3000 [size=256]
        Expansion ROM at b2020000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] #10 [0001]
        Capabilities: [80] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000

0000:03:00.1 Display controller: ATI Technologies Inc: Unknown device 5569
        Subsystem: ATI Technologies Inc: Unknown device 0313
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 0x10 (64 bytes)
        Region 0: Memory at b2010000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] #10 [0001]

```

Xorg.0.log (attached)

---

### Post by patrick295767 on 2006-06-12
We are both victims kind of the same problem : Dapper :-) 

[http://www.ubuntuforums.org/showthread.php?t=194359](http://www.ubuntuforums.org/showthread.php?t=194359)

No way to make use of my pc ... either ... 

Greetings to you,

---

### Post by Fry-kun on 2006-06-12
[QUOTE=patrick295767]We are both victims kind of the same problem : Dapper :-) 

[http://www.ubuntuforums.org/showthread.php?t=194359](http://www.ubuntuforums.org/showthread.php?t=194359)

No way to make use of my pc ... either ... 

Greetings to you,[/QUOTE]


So much for Long Term Support.. this has got to be some sort of a record -_-

At least I have X running -- but still can't run any overlay/opengl apps :(

---

### Post by lamego on 2006-06-12
You problem with running fglrxinfo is because you are running it with a different user from the one used by X. I hope you are not using root as your default user, and it is not sane to run other commands as root when they don't need it (which is your case with fglrxinfo ).

---

### Post by wpshooter on 2006-06-12
[QUOTE=Rackerz]Ok first you will need open up your xorg.conf, do this by opening a terminal and typing;
```
sudo gedit /etc/X11/xorg.conf
```

Then you need to go to this line in the file;

Under that line you will see 'Driver "ati"' change it to;
```
fglrx
```
Then reboot.[/QUOTE]

When I follow this procedure on my computer, when this file is opens it is empty, i.e. nothing in it.  

What does that mean ?

Thanks.

---

### Post by elbryan on 2006-06-12
If you are intereset with installing ATI drivers under linux there's an italian guide at our wiki..

The url for my co-national (for anyone else you have simply to follow the command to prompt) is [http://wiki.ubuntu-it.org/Enable3DAtiRadeon%28fglrx%29]("http://wiki.ubuntu-it.org/Enable3DAtiRadeon%28fglrx%29")

---

### Post by Fry-kun on 2006-06-12
***
3 years later
me: yay, I finally know enough Italian to install my video card!
***

:D

---

### Post by elbryan on 2006-06-12
I'm so glad that helped you :P

---

### Post by Fry-kun on 2006-06-12
sorry, gotta find SOME way(s) of letting out the frustration -_-'

I'll try your method of course, when I get a moment

---

### Post by WorLord on 2006-06-12
How very interesting.  My Dapper experience is the opposite: none of the Breezy drivers would work very well on an ATI card, and it all works great now.  The proprietary drivers even offer some Dual-Head stuff I'm making use of here.

---

### Post by Fry-kun on 2006-06-12
After reading the IT guide (thanks to BabelFish in my ear), I decided to try the main wiki made for ATI.
Previously, I only tried the included driver - but this time I went through with the manual solution (same driver supposedly...).
Everything works now!
Goodbye, and thanks for all the help!

P.S. j/k about goodbye, but as long as I'm doing HHGttG references... :D

P.P.S. OP, try the manual method and post the results - might work for you too.

---

### Post by DonQuixote on 2006-06-15
Fry-kun,

Could you post a link to that wiki guide?  I've gone to so many guides and links I may have seen and tried it, but I'm willing to take a look to find out.

Thanks!

---

### Post by Fry-kun on 2006-06-15
[QUOTE=DonQuixote]Fry-kun,

Could you post a link to that wiki guide?  I've gone to so many guides and links I may have seen and tried it, but I'm willing to take a look to find out.

Thanks![/QUOTE]

Sorry, I didn't realize that it was kinda hard to find until now.

The guide is here: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by patrick295767 on 2006-06-21
[QUOTE=Fry-kun]So much for Long Term Support.. this has got to be some sort of a record -_-

At least I have X running -- but still can't run any overlay/opengl apps :([/QUOTE]
 
I have the ati card working with Ati module, but unfortunately for gaming, I didnt really have time yet to work on this pc to have a decent glxgears result. 
 
I can still play games like age of empires 2, starcraft ... 
So, that's not that bad at all :-)
...
Dapper is really faster than Breezy. I really like this Dapper, but ati cards ... I have doubts.
All my nvidia cards are working sooo greatly under Dapper !! 100% working wihtout any problems !
  
There is this thread here too: [http://www.ubuntuforums.org/showthread.php?p=1164325#post1164325](http://www.ubuntuforums.org/showthread.php?p=1164325#post1164325)

---

