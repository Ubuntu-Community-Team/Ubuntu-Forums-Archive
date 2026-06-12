---
title: "Need some help with choppy sound issue in ZSNES 1.51."
date: 2008-04-21
forum: Gaming &amp; Leisure
---

### Post by thegreatdestroyer on 2008-04-21
I never had any issues with ZSNES on the Windows box but I'm having choppy sound on the Ubuntu box. I'm sure it's not my soundcard as I've read some articles and it seems many people are having sound issues with version 1.51. One guy said he was having issues very similar to mine and enabled libao as an alternative to SDL for sound. Said to check zsnes --help and see -ad flag. I'm not sure if this would help me or not. But I do wanna get this resolved and any help would be appreciated. I used a deb package to install ZSNES and below I'm posting my system specs.

SYSAM4007           AM4007 SEMPRON
                    2200+/256/

MB-BM6100M7         BIOSTAR SKT754 CE 1G/MCP51 MB

CP-ASE2800R         AMD SEMPRON 2800 CPU (RTL)

RD-256MB400         256MB DDR 400MHZ

HDWD80BB            WD 80GB 7200RPM WD80BB

CR-SOX220E          SONY 52X32X52 CDRW IDE BLK 
                    CRX230ED-B2

FX-T306G            56K V.92 PCI HARDWARE MODEM

CS-M161             MICROTEL MicroATX 3-2

SWL5-F01            LINSPIRE 5.0 OPERATING SYSTEM

KB-EA107KB          107-KEY STANDARD BLACK PS/2

KB-HK100/360B       MOUSE BLACK 

BOX-M05             MICROTEL SMALL SIZE SHIPPING BOX W/FOAM

SYSPC               TESTING AND ASSEMBLY PC

---

### Post by thegreatdestroyer on 2008-04-22
I ran ZSNES through the terminal like so:

zsnes -ad alsa

I went into sound menu in gui and played with sample rate. 48000HZ was perfect. I used Gaussian interpolation and hi quality Low Pass. Tested with Final Fantasy V and Final Fight 3. Both worked great. After quitting the emulator and terminal and reopening again a couple of minutes later the problem was back, but the settings were the same. I noticed in the terminal when I'd exit sound menu and hit esc to return to game that when it started back up this message continually and rapidly came up in terminal:

ALSA: underrun, at least 0ms.

I've been able to get sound working perfectly one other time, but these seem like strokes of luck, very hit and miss. If sound will work perfectly once then there's a way to keep it working perfectly. I really need some help with this. I'd prefer if someone could chat me over yahoo messenger so we could straighten this out, but any help would be greatly appreciated.

---

### Post by thegreatdestroyer on 2008-04-22
Bump

---

### Post by mastahkillah666 on 2008-04-23
When you launch a game, pause the emulator by pressing the "ESC" (escape) key and then, a second or two later, unpause it by pressing the same key again and your problem should be gone.  This is due to the fact that the Emulator causes a buffer underrun to the ALSA driver in its first version (not the ALSA09 driver).  Try to lower the sampling rate or the effects and see if the sound still cracks.  Hope this helps.

See ya around the forums...

---

### Post by acoustibop on 2008-04-25
Do 'zsnes --help' in a terminal to print a list of switches for ZSNES, thegreatdestroyer; this will include a list of the various audio drivers.  Start ZNES with 'zsnes -ad <your choice of driver>' until you find the one that works best for you.

Then you can select it permanently by editing ~/.zsnes/zsnesl.cfg and changing the libAO driver to the one you want to use.

---

### Post by CaptainPedro on 2008-04-26
Im having the same problem with choppy sound.

The only way I can get any sound is when I do "zsnes -ad sdl". I went in to the zsnesl.cfg file and changed it to use sdl, but now the sound is all choppy and crackly. I tried telling zsnes to use alsa, but then there was no sound at all.

---

### Post by Cresho on 2008-04-26
Mines runs just fine flawlessly!  hardy heron os

all I did was install in synaptic
libsdl1.2debian-all

and change the zsnes launcher or try in terminal for start

zsnes -ad sdl

I can play all with no sound.  If I just run zsnes, there is no sound at all and I looked day and night.  As a matter of fact, I had another method but lost it in the update.  I can't seem to find my notes. :popcorn:

here is another post from a guy who says installing ess fixes 
[http://ubuntuforums.org/showthread.php?t=733387garbled](http://ubuntuforums.org/showthread.php?t=733387garbled) sound...and i believe him cuz i had this expirience in another pc.

---

