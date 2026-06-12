---
title: "Why can I not get a single game emulator to work in Ubuntu 11.10?"
date: 2012-02-12
forum: Emulators
---

### Post by guyver_dio on 2012-02-12
I've been trying for 3 days now, I've been wanting to play old nintendo 64 and ps1 games again so I've been looking for nintendo64 and playstation emulators. 

I've tried probably every nintendo64 emulators out there, both native and windows ones through wine. Most of the time I can't even get the emulators to install and when I do they mostly don't open. The few that do I'll do to run a rom and 100% of the time the emulator just closes. 

Does anyone have any emulators for these consoles running on ubuntu 11.10?

---

### Post by uRock on 2012-02-12
Moved to *"Emulators"*

---

### Post by josephmills on 2012-02-12
I think that psx is in the repos 


```
sudo apt-get install pcsx-df
``` if that won't work try 
```
sudo apt-cache search pcsx 
``` then find the package that you are looking for. 

Ps2 emulator 

```
sudo apt-add-repository ppa:gregory-hainaut/pcsx2.official.ppa
```
then 
```
sudo apt-get update 
```
then 
```
sudo apt-get install pcsx2
``` there are plugins and bios that you are going to need for both pcsx and pcsx2 


PSP emulator 

you can find out more about this at 
[http://jpcsp.org/](http://jpcsp.org/)

N64 And others 


[http://www.playdeb.net/updates/Ubuntu/10.04/?category=Emulator](http://www.playdeb.net/updates/Ubuntu/10.04/?category=Emulator) 




let us know how it goes or if you get hung up on anything.

---

### Post by josephmills on 2012-02-12
I would like to put up a warring about the PS2 emulator YOU must have good hardware to run this. a good gpu and good cpu. that said use at your own risk

---

### Post by thatguruguy on 2012-02-13
My daughter is playing a game on Dolphin-Emu right now.

I also have pcsx-r and Mupen-64 plus installed, and they run without any problems. Do you have the correct (proprietary, if necessary) drivers installed for your graphics hardware?

---

### Post by guyver_dio on 2012-02-15
Thanks for the responses. I decided to do a reinstall of ubuntu cause my install was all messed up from trying to make programs work, mupen64plus is now working so I'm guessing I must have messed with a file it needed.

Wow I didn't even know they had a playstation 2 emulator, but the ppa says it's for 32-bit OS only, are there any ports of this for 64-bit or any 'hacky' ways to get it working on 64-bit?

---

### Post by Thebuntuway on 2012-03-13
Have you trying download these. I see many people does work with it..
-----------------------------------------------------------
[http://www.codeweavers.com/](http://www.codeweavers.com/)
-----------------------------------------------------------
Good luck bro!..hope these helps!):P

---

### Post by wesaus35 on 2012-04-12
[http://ubuntuforums.org/showthread.php?t=1908483](http://ubuntuforums.org/showthread.php?t=1908483)

This thread lists a ton of emulators that work on Ubuntu, very helpful list :D

---

### Post by honeybear on 2012-05-08
there is such a project. it is xmess, mostly nothing works wiht it ;)

---

