---
title: "pSX emulator slow framerate in linux"
date: 2008-07-13
forum: Gaming &amp; Leisure
---

### Post by epyon22 on 2008-07-13
I have just begun to use playstation emulators in linux and i stumbed apon pSX a very simple ez to use emulator. Though when i run it every thing is very slow. The computer im running it on is a 2.0 ghz turion with dynamic frequency. I have tested psx in windows and it works flawlessly 60 fps whole time. Though in linux its at least half the fps.

My guess is pSX reconizes my processor as a 800 mhz processor and thats it either that or somthing else is limiting it maybe sound or graphics processors. any sugestions or tips would be helpful

btw my full specs
2.0 ghz amd turion 64
ati x700 mobile
some via sound card(lol)
running on 8.04 hardy 
kubuntu

---

### Post by acoustibop on 2008-07-13
Are you using the fglrx driver for your videocard, epyon22, or the free ati driver?

---

### Post by epyon22 on 2008-07-13
fglrx though i dont see how that would affect it too much cause isnt pSX mainly cpu intensive

---

### Post by acoustibop on 2008-07-14
It is, but using the fglrx driver does seem to give improvements over the ati driver.  Could you post the results of fglrxinfo, please?

Yes, AFAIK pSX does only use one core of a multi-core CPU.  It might be a good idea to post this in the [pSX official forum]("http://psxemulator.proboards54.com/"), as it's generally assumed that even one core of any multi-core processor should be able to run pSX fine, and if this is not so, pSX Author ought to know.

---

### Post by epyon22 on 2008-07-14
> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

yeah I just signed up on the pSX forums i will be posting there maybe later today.

---

### Post by acoustibop on 2008-07-14
Ah, that's good, epyon22.  However, your fglrx driver is not properly installed: it should not not be using the Mesa driver for OpenGL.  See my result:```
 fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 XT
OpenGL version string: 2.1.7412 Release
```
Do glxinfo and post the first few lines, please; I strongly suspect you won't have direct rendering enabled.  This will impact on pSX' performance.  Which version of the fglrx driver are you using, and how did you install it?

---

### Post by epyon22 on 2008-07-14
Ok well tried glxinfo and it showed that it wasnt installed. I used envy to install my ati driver its showing version 8.47.3 in the catalyst control center under info.

---

### Post by acoustibop on 2008-07-14
I also have the 8.47.3 driver, except that I simply installed it via Hardware Drivers (don't know if it's the same name in Kubuntu?).  8.47.3 is actually the driver it installs.  While Envy works for some people, it messes up for some; Hardware Drivers, on the other hand, shouldn't mess up at all; it's an integral part of Hardy.

If you can get rid of the driver without messing your system up, I'd do so; then reinstall it as I suggested.  The only thing you need to do after letting Hardware Drivers install the driver for you (after rebooting) is```
sudo aticonfig --initial -f

then

sudo aticonfig --overlay-type=Xv
```.

---

### Post by epyon22 on 2008-07-14
I'll see what i can do i have my home dir on a different partition so i might just reinstall the root partition

---

### Post by epyon22 on 2008-07-14
> Ha...well one extreme to another now it runs too fast and its defiantly because of the variable processor speed because if i change it to "power saving mode" it goes the right speed but lags up a bunch in other parts. :( any help here?

btw what exactly did those commands do? i did not run them.



nvm! i got it working great i had to redo every thing again cause i screwed up my ps3 controller it wouldn't register. So now ive got ps3 dual shock 3 working over bluetooth and a working ps1 emulator on my laptop portable ps1 thx alot man

---

### Post by acoustibop on 2008-07-15
> **epyon22 said:**
> btw what exactly did those commands do? i did not run them.

Very simple: the first command sets up a configuration file for the fglrx driver, and the second sets an appropriate overlay mode: won't make any difference for games (probably) but will make all the difference if you want to run a TV application - or possibly some DVD players.

---

