---
title: "epsxe won't load games from cdrom"
date: 2009-03-17
forum: Gaming &amp; Leisure
---

### Post by myromance123 on 2009-03-17
Hey there I followed this guide :
  [Install ePSXe Playstation Emulator (Version 2)]("http://ubuntuforums.org/showthread.php?t=612021")

I'm running Ubuntu 8.04 (32-bit). Radeon x1650 graphics card (using x1600 9.2 driver), 1.5GB ddr1 ram and a 2.3Ghz Pentium 4.
  I've played ps1 games on a computer with lower specs before so I know thats not the problem.

I have epsxe set up. The only problem was that I do not know how to configure Cdrom.
  I tried using /dev/cdrom, /cdrom, /cdrom0, computer:/// and a whole bunch of other wacky stuff.

 Here's the output from the terminal when I try to run from Cd-Rom:
```
yusuf@yusuf-desktop:~$ epsxe
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios//SCPH1001.BIN]. 
 * Init internal cdrom ... ok
CD read toc header failed (25)
 * First/Last track: 7 2
 * Track 1: CD get track start failed (25)
 (AUDIO) - Start 0: (00,00,00) 
 * Track 2: CD get track start failed (25)
 (AUDIO) - Start 1: (00,00,00) 
CD(0,2,16) read ioctl failed (25)
CD(0,17,59) read ioctl failed (25)
CD(0,17,60) read ioctl failed (25)
 * NTSC cdrom detected. 
 * Init gpu[0][libgpuPeopsSDL.so.1.0.16] 
/usr/local/bin/epsxe: line 6: 15451 Segmentation fault      ./epsxe $*
yusuf@yusuf-desktop:~$
```
  
  I want to run my ps1 games from CDs. My ps1 is too old and can't read most of them anymore. My CDs have no scratches and I used to play them on Windows XP. I don't and cannot dual boot and there are no Windows computers in the house so that is not an option.

 I have checked my Dual layer DVD-ROM drive and it works fine, reads everything.

Does anyone know what the problem is?
  I do not know how to decipher the output from the terminal above.

---

### Post by namaku0 on 2009-03-17
It seems ePSXe Seg Faulted right after initializing
the GPU plugin. Try it with other GPU plugins:
[http://www.pbernert.com/html/gpu.htm](http://www.pbernert.com/html/gpu.htm)

Maybe you want to try pSX emulator a try too:
[http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/)

---

### Post by myromance123 on 2009-03-17
Hey thanks for the fast reply. Okeh I'm trying out other gpus now.

 I tried pSX before, it crashes just like epsxe.

---

### Post by myromance123 on 2009-03-17
Hey thanks dood, I went to config > video and changed it to Pete's MesaGL Driver 1.76 instead of the P.o thingy and it ran tekken just fine.

 Although I can't run Chocobos dungeon2 or suikoden 2, but that seems to be a problem with my dvd drive not reading them.
  Thanks dood.

 Now I'm just gonna try and find out how to use Logitech Rumblepad 2 with epsxe and probably rip some of the ps1 games and see if they work that way.

:D

---

### Post by myromance123 on 2009-03-17
Cool, now I can play ps1 games again xD
  With Logitech's RumblePad 2 also!
And nice sound~

 For those who read this in the future, be you guest or member running ubuntu 8.04 32bit, this is what I did to get myself up and running:

1. I followed Felsons [Install ePSXe Playstation Emulator (Version 2)]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=612021") to get epsxe up and running (best to type the commands one by one to know where anything goes wrong)

2. I searched on google for the bios "scph1001.bin" and found a solid working one (after which I inserted it into epsxe's bios file).

3. I used PSXIM to make .bin files of my ps1 cds to make it easier to play them. I used this [Back up your PlayStation games using PSXIM (easy GUI)]("http://ubuntuforums.org/showthread.php?t=664656") thread to install and familiarise myself with how PSXIM works.

I use Pete's MesaGL Driver 1.76 for the gpu (config > video and select it)
I use P.E.Op.S. OSS Audio Driver 1.9 for sound (with pulseaudio on, I do not experience any bad sound quality)
For (config - cdrom) I use /media/cdrom0 .

For the Logitech Rumble Pad 2 I just plugged in the controller, went to config> Ext. Game Pad and selected each button and pressed the appropriate button on the controller and that was it.
 I have no other software or any type of settings for my logitech controller, it just works.

Only prob I experience is in fullscreen mode (no image), so instead I use windowed but I give the width and size appropriate values to give it the fullscreen feel (it varies with each monitor I think, and I'm using an old type hehe)

To load the games you made .bin files of using psxim, open epsxe then go to File > Open ISO and search for the .bin file of the game (where ever you saved it) open it and voila it should run~
 Give the blackscreen a second or two and then it should start

Woot go gaming xD

---

