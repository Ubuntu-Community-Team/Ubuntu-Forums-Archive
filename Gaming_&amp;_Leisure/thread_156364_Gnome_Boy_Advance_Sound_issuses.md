---
title: "Gnome Boy Advance Sound issuses"
date: 2006-04-06
forum: Gaming &amp; Leisure
---

### Post by slipk487 on 2006-04-06
i have no sound when running GBA can anybody help

---

### Post by clarjon1 on 2006-04-07
OK, let's run thru a quick checklist:
1) Is your soundcard configured?
2) what emulator are you using?  Does it have sound capabilities?
3) if you answered VBA, and yes to #2, then go to the vba config file, and make sure that it has sound turn on.
4) Close all applications that use soundcard
5) Make sure sound is unmuted
6) Turn up volume
7)Make sure speakers are plugged in and turned on.
8)Turn off the sounds that Ubuntu makes normally--This can clog up the sound, which will disable sound for blah, blah, blah...

good luck!

---

### Post by slipk487 on 2006-04-07
yes and i and using vba under Gnomeboy Advance

---

### Post by slipk487 on 2006-04-07
i cant find it

---

### Post by sudomania4 on 2006-04-08
I have no sound either. I use visualboyadvance run by the command "gvba". It has sound capabilities.

---

### Post by slipk487 on 2006-04-08
that didnt work for me and heres my configuration file 

```
captureFormat=0
saveDir=/home/slipk487/Desktop/2nd HDD/GBA GAMES
batteryDir=/home/slipk487/Desktop/2nd HDD/GBA GAMES
Joy0_Left=0114
Joy0_Right=0113
Joy0_Up=0111
Joy0_Down=0112
Joy0_A=007a
Joy0_B=0078
Joy0_L=0061
Joy0_R=0073
Joy0_Start=000d
Joy0_Select=0008
Joy0_Speed=0020
Joy0_Capture=0125
Motion_Left=0104
Motion_Right=0106
Motion_Up=0108
Motion_Down=0102
video=1
fullScreen=0
throttle=0
filter=A
gbFrameSkip=0
frameSkip=0
ifbType=2
autoFrameSkip=0
colorOption=1
borderAutomatic=0
soundQuality=1
soundVolume=3
soundEnable=30f
soundReverse=0
soundOff=0
soundEcho=0
soundLowPass=0
saveType=0
biosFile=none
flashSize=0
emulatorType=0
showSpeed=1
rewindTimer=0
showSpeedTransparent=1
rtcEnabled=1
useBios=0
skipBios=0
disableStatus=0
pauseWhenInactive=1
agbPrint=0
borderOn=0
disableMMX=0

```

---

### Post by SlCKB0Y on 2006-04-08
OK. ive never used a game boy advance emu, but here are some general things to check. 

Does you GBA emu use LibSDL? i fyes ..What sounds drivers are you using? ALSA?

Do you have ESD running?

OK, Make sure you have libsdl1.2debian-alsa installed.

Also maybe either try turning off esd, or installing libsdl1.2debian-esd instead.

Its hard to help without more info.

---

