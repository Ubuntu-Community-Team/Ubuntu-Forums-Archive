---
title: "PSX fans will LOVE this"
date: 2007-01-04
forum: Gaming &amp; Leisure
---

### Post by chronusdark on 2007-01-04
if you have tried the emulator called pSX you will know its the best playstation emu for windows but now it may be soon coming to linux

[check this out]("http://psxemulator.proboards54.com/index.cgi?board=support&action=display&thread=1165882851&page=5")

make sure you let pSX Author know how you feel

---

### Post by gaspar on 2007-01-04
Hmm... tought the best was epsxe...
but I´ll give this pSX a try ;-)

---

### Post by MaximB on 2007-01-04
I'm waiting for a working PS2 emulator to be ported to Linux

---

### Post by chronusdark on 2007-01-04
> **gaspar said:**
> Hmm... tought the best was epsxe...
but I´ll give this pSX a try ;-)

pSX is aimed at delivering HIGH compatibility and creating a genuine psx experience (ie. no fancy filters) just the basics and standard resolutions but it plays near flawlessly in windows and fairly good in wine so im expecting this to kick ***

---

### Post by rolando2424 on 2007-01-04
> **MAXDDARK said:**
> I'm waiting for a working PS2 emulator to be ported to Linux

Well, I'm still waiting for one that works great :D

---

### Post by damvcoool on 2007-01-04
well i have the one that comes with ubuntu 6.10 PCSX and downloaded some plugins, and even i somehow got the bios from the Playstation, the thing is that all my old PSX games are playble and with better graphics than the PlayStation itself :P i can Pack and post here my .pcsx folder so you can compare. (note i wont post the bios because of legal issues)

---

### Post by anders.149 on 2007-01-07
In case someone wonders, pSX works great with wine! I played Final Fantasy VII using pSX and wine a few months ago. Thumbs up!

Btw, does anyone know how to make proper backup of Playstation disc's in linux? I can't get my games to rip succesfully in linux. =/

---

### Post by po0f on 2007-01-07
anders.149,

This is a script I wrote to rip PSX images, it might work for others as well.  You'll need [cdrdao](http://packages.ubuntu.com/edgy/otherosfs/cdrdao) installed for it to work.  First, you need to do a little setup; namely, which CD drive to use (command you type is bolded, don't really know why sudo access is needed):
```
[FONT="Courier New"]$ **sudo cdrdao scanbus**
... snipping useless program output ...
ATA:1,0,0       TSSTcorp, CD/DVDW SH-S182M, SB02[/FONT]
```
We're interested in the first field of the output, ATA:1,0,0.  This is the way cdrdao names the devices.  You might have more than one device in the output; just use the one that you will rip PSX CDs with.

Now, the script:
```
[FONT="Courier New"]#!/bin/bash

if [[ -z "$1" ]]; then
    echo -e "Usage: `basename $0` <filename>"
    echo -e "Error: No filename specified."
    exit 1
fi

cdrdao read-cd --device **ATA:1,0,0** --driver generic-mmc-raw --read-raw --datafile $1.bin $1.toc

exit 0[/FONT]
```

Save this script as 'mkpsximage' in /usr/local/bin **and give it execute permission**.  You'll need sudo access to do this.  (Change the bolded portion to whatever drive you want to use.)  When you use the script, you will need to specify a base filename to use for the created BIN/TOC files.  Say you were ripping Final Fantasy VII, disc one:
```
[FONT="Courier New"]$ mkpsximage ff7-d1[/FONT]
```

When the script is finished, you should have two files in the current directory, 'ff7-d1.bin' and 'ff7-d1.toc'.

HTH

[EDIT]

Added the bold part.

[EDIT 2]

Final line in the script should be 'exit 0', not 'exit 1'.  :)

---

### Post by llirium on 2007-01-09
Thanks a lot for the useful script, po0f.  Worked like a charm on my epsxe. ^^

---

### Post by anders.149 on 2007-01-17
I finally had the time to try your script po0f and it's wonderful! Now both ePSXe and PCSX run my game's that's made entirely with Linux which feels good. No more Windows for PS1 emulation I hope. ;)

One problem remains though, I can't get sound to work in either ePSXe or PCSX. I have tried both Peops OSS and ALSA plugins as well as Eternal. The sound stutters. I have tried to increase the sound buffer in Eternal but it doesn't get any better. 

Thanks po0f! =)

EDIT: Nevermind! pSX WIP for Linux has been released, it works MUCH better than any other playstation emulator for Linux even in it's WIP state! Try it out! 

Get it from the official site:
[http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1170069898&page=1](http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1170069898&page=1)

---

### Post by bebop_tango on 2007-03-27
Hey, pSX is no longer a WIP...! psX 1.11 for Linux has been released and can be downloaded from [here]("http://psxemulator.gazaxian.com/pSX_linux_1_11.tar.bz2").

:lolflag: 

This IS the best PSX emulator I've ever tried... works with many games ePSXe didn't play well and the best of all... doesn't need any plug-ins! So it's pretty easy to set up and use.

The only thing I miss is a scanline video blitter... but it's nothing really.

;)

---

### Post by second.exodous on 2009-02-13
Just wondering, after you make backups like this is there a way to burn that backup to a disk and play in a playstation with a modchip?

---

