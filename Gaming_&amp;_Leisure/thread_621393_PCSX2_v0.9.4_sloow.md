---
title: "PCSX2 v0.9.4 sloow"
date: 2007-11-23
forum: Gaming &amp; Leisure
---

### Post by mtxcoll on 2007-11-23
Hi, I just downloaded and successfully compiled the SVN version of PCSX2, version 0.9.4. I'm trying to get Final Fantasy XII to run at a playable framerate (20+ fps) but so far have had little success. Even the BIOS runs only at 12 fps, and the game itself runs at <5 fps. Is my hardware even up to snuff? I have an HP Pavilion dv5163cl with Intel Core Duo Processor T2300 @ 1.66 GHz, 1 GB memory, and a Geforce Go 7400 graphics card.

My settings (pcsx2.cfg):
```

Bios = SCPH-70012_BIOS_V12_USA_200.bin
Lang = en
PluginsDir = plugins/
BiosDir = bios/
Ps2Out = 1
ThPriority = 0
Mcd1 = 
Mcd2 = 
GS = libZeroGSoglr.so.0.96.2
SPU2 = libspu2PeopsOSS.so.1.6
CDVD = libCDVDisoEFP.so
PAD1 = libZeroPAD.so.0.1.0
PAD2 = libZeroPAD.so.0.1.0
DEV9 = libDEV9null.so
USB = libUSBnull.so
FW = libFWnull.so
Options = 8f3
Patch = 1
varLog = 0

```

zerogs.ini:
```

interlace = 2
aliasing = 0
bilinear  = 0
options = 0
gamesettings = 0

```

By the way, sorry about posting here, but for some reason I can't access the ngemu forums (they banned my e-mail address although I've never registered there before).

---

### Post by hikaricore on 2007-11-23
IMHO you would need a much faster processor to get a good framerate.
My dualcore which is overclocked to 2.4ghz (for some reason pcsx2 shows the wrong cpu speed O.o) gets between 30-50fps with dualcore optimization flags checked, and it still drops below 30 sometimes.

Did you enable these options?

[IMG]http://img.photobucket.com/albums/v414/hikari_corgan/pcsx2.png[/IMG]

PS2 emulation is still very very young and for most very slow.

---

### Post by hikaricore on 2007-11-23
You have a PM there buddy :p

Hopefully my suggestion helps.

---

### Post by Sockerdrickan on 2007-11-23
64bit really helps too.

---

### Post by hikaricore on 2007-11-23
Even when you're running 32bit code?  :p

---

### Post by Sockerdrickan on 2007-11-23
(borat style)... noooot XD

---

### Post by mtxcoll on 2007-11-24
> **hikaricore said:**
> IMHO you would need a much faster processor to get a good framerate.
My dualcore which is overclocked to 2.4ghz (for some reason pcsx2 shows the wrong cpu speed O.o) gets between 30-50fps with dualcore optimization flags checked, and it still drops below 30 sometimes.

Did you enable these options?

[IMG]http://img.photobucket.com/albums/v414/hikari_corgan/pcsx2.png[/IMG]

PS2 emulation is still very very young and for most very slow.

Thanks for the help! Unfortunately I've checked all the flags and tried the suggestion you gave me in the PM with no success; a quick glance at my system monitor tells me that the performance is really bottlenecked by the CPU, with both cores running at 100% :sigh: I guess I'll just have to wait until I have a more powerful laptop then.

---

### Post by barius on 2007-12-05
You say your CPU is a Core Duo T2300?  That is the older Core version which is only about as fast (clock for clock) as the AMD X2 series.  The Core2 Duo model is newer and is 20-40% faster with PCSX2.

Your only hope is if your laptop allows you to overclock your CPU.  Even then you'll be struggling to reach 20fps in FF12 since that game is very demanding.  On the bright side, you should be able to play FFX at around 30fps.

BTW, turn off the Compiz effects while playing, they can seriously impact performance.

---

### Post by hectic1 on 2008-04-07
youre pc just isnt fast enough,will never be fast enough even if you try it in winxp,srry about that,you cant do anything about it,even if you did smth wrong you wont get 20 fps if you do it right

---

### Post by Ioky on 2008-04-08
Well, Personally I don't think that is the CPU's problem. at least not just the cpu. The reason I say that is me and cousin both own a IBM desktop run by a core 2 Duo1.86GHz cpu. so when he play FFX on it, he think that is a big slow, but it 100% playable. However, when he play the on a his other computer the game well too fast, that he can't even control it. and he has to limited down the fps in order to play it. Well, he get a better graphic card and more ram on the other computer, So. And he have been finish a few game under PS2 EMU. So 

By the way his setting is 1.86GHz core 2 Duo, 2G of ram, and nvidia 7600GT @ 256 vram. 

close to mine except I am using 2.4Hz core 2 Duo. hehe

---

### Post by TenPlus1 on 2008-04-08
You could try running the nvidia-settings in terminal and turning ON Vsync for your gfx card...  This will still give you a good framerate playing 3d stuff, but it doesnt overload the processor by doing so...

---

