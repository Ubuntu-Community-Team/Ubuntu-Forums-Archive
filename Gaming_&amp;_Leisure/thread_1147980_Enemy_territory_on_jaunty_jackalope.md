---
title: "Enemy territory on jaunty jackalope"
date: 2009-05-03
forum: Gaming &amp; Leisure
---

### Post by adjock12 on 2009-05-03
Hey,

I am having problems running my enemy territory game. I have just recently updated to Jaunty jackalope and am finding there are still quite a few bugs. one that is really annoying me though is with enemy territory. I have reinstalled it and that didn't help at all. Here is the code i get when I load the game through terminal.

```
alex@Alex-laptop:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/alex/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
X Error of failed request: BadMatch (invalid parameter attributes)
  Major opcode of failed request: 1
  Minor opcode of failed request: 0
  Serial number of failed request: 41
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 42
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 43
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 8
  Minor opcode of failed request: 0
  Serial number of failed request: 44
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 12
  Minor opcode of failed request: 0
  Serial number of failed request: 45
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 48
X Error of failed request: BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request: 136
  Minor opcode of failed request: 7
  Serial number of failed request: 53
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 154
  Minor opcode of failed request: 26
  Serial number of failed request: 53
Received signal 11, exiting...
Segmentation fault

```

Any suggestions how to fix this would be great thanks.

---

### Post by omegvermelho on 2009-05-09
Hey adjock12 this is what i did and its working good so far (except 5 button mouse.cfg but ill get there) anyway here it goes...

I started by following this tutorial [https://help.ubuntu.com/community/EnemyTerritory ]("https://help.ubuntu.com/community/EnemyTerritory")

Make sure to copy/paste the et etded files from the 2.60b Patch (MAY ure runing March) into your /usr/local/games/enemy-territory/etmain 



I also use a GameBrowser with ET called XQF - [http://www.linuxgames.com/xqf/index.shtml](http://www.linuxgames.com/xqf/index.shtml) its very handy you should try it after the ET install

---

### Post by omegvermelho on 2009-05-09
This one looks really nice also - [http://ubuntuforums.org/showthread.php?t=662770](http://ubuntuforums.org/showthread.php?t=662770) check the List go to Enemy Territory and follow the steps....

---

### Post by Burneddi on 2009-05-10
OK as having the same problem and still lacking to find the solution I can't really help, but well:

You probably have a Radeon card. That is the problem.
See, for some reason, 3D acceleration doesn't work at all for some Radeon cards (or the drivers) in 9.04. Seems like the radeon driver and radeon-hd driver are concerned.. Not sure of fglrx.

So, check what driver you're using from /var/log/Xorg.0.log :
```
gedit /Var/log/Xorg.0.log
```
There should be something like
```
(II) LoadModule: "radeon"
```
if you have a Radeon video card. If that is the case, there's pretty much nothing you can do except revert to 8.10 until the bug is fixed. It should work in 8.10 no problem..

---

### Post by ardoaamch on 2009-05-10
This is probably a problem with your video card drivers.

---

### Post by meborc on 2009-05-11
> **omegvermelho said:**
> Hey adjock12 this is what i did and its working good so far (except 5 button mouse.cfg but ill get there) anyway here it goes...

I started by following this tutorial [https://help.ubuntu.com/community/EnemyTerritory ]("https://help.ubuntu.com/community/EnemyTerritory")

Make sure to copy/paste the et etded files from the 2.60b Patch (MAY ure runing March) into your /usr/local/games/enemy-territory/etmain 



I also use a GameBrowser with ET called XQF - [http://www.linuxgames.com/xqf/index.shtml](http://www.linuxgames.com/xqf/index.shtml) its very handy you should try it after the ET install


if you need mouse buttons to work, have you tried this? [http://www.hirntot.org/index.php?option=com_content&view=article&id=96&Itemid=108](http://www.hirntot.org/index.php?option=com_content&view=article&id=96&Itemid=108)

---

### Post by DustofDust on 2009-05-11
since the upgrade from 8.10 to 9.04 the sound does not work anymore.

i used [http://www.playdeb.net/](http://www.playdeb.net/) to install rtcw:et

i tried to switch from 22khz to 44khz but this didnt help as suggested here
[http://adammichaelroach.com/blog/050409/wolfenstein-enemy-territory-ubuntu-linux-jaunty-jackalope-904](http://adammichaelroach.com/blog/050409/wolfenstein-enemy-territory-ubuntu-linux-jaunty-jackalope-904)

---

### Post by meborc on 2009-05-11
> **DustofDust said:**
> since the upgrade from 8.10 to 9.04 the sound does not work anymore.

i used [http://www.playdeb.net/](http://www.playdeb.net/) to install rtcw:et

i tried to switch from 22khz to 44khz but this didnt help as suggested here
[http://adammichaelroach.com/blog/050409/wolfenstein-enemy-territory-ubuntu-linux-jaunty-jackalope-904](http://adammichaelroach.com/blog/050409/wolfenstein-enemy-territory-ubuntu-linux-jaunty-jackalope-904)

[http://www.hirntot.org/index.php?option=com_content&view=article&id=97&Itemid=109](http://www.hirntot.org/index.php?option=com_content&view=article&id=97&Itemid=109) - this works on jaunty, tried it today :)

---

### Post by DustofDust on 2009-05-11
> **meborc said:**
> [http://www.hirntot.org/index.php?option=com_content&view=article&id=97&Itemid=109](http://www.hirntot.org/index.php?option=com_content&view=article&id=97&Itemid=109) - this works on jaunty, tried it today :)

does not work for me because

> Edit the start routine of ET
Code:

sudo gedit /usr/local/bin/et

Find:  this file was was not there!

again, i used the [http://www.playdeb.net/](http://www.playdeb.net/) repo for installation!

---

### Post by ardoaamch on 2009-05-11
Are you using any other programs that play audio either while you play ET or before?  I am the author of that blog post above.  The only thing I did to get audio working was to set the sound to ultra-high.  Also you may try running this command right before you play ET:

```
killall -9 pulseaudio
```

Please post back with your results.

---

### Post by DustofDust on 2009-05-12
before i played music but not while. setting et to ultra high does not work as it not saved in et,

```
killall -9 pulseaudio
```
this works and i have sound again in et. thank you very much!

strange that it does not work with 22khz but with 44khz.

seems i need to run every time the code.

---

### Post by ardoaamch on 2009-05-12
Cool.  I'm glad it worked for you.  Pulseaudio is a strange beast.  Don't even try to understand it. :)

If anyone else is having troubles with ET, please feel free to post your questions here.  I'm happy to help.

---

### Post by DustofDust on 2009-05-12
i looked a little bit around and found this.

[http://pulseaudio.org/wiki/PerfectSetup#RTCWEnemyTerritoryTrueCombatEliteQuake3](http://pulseaudio.org/wiki/PerfectSetup#RTCWEnemyTerritoryTrueCombatEliteQuake3)
> RTCW / Enemy Territory / True Combat Elite / Quake 3

To use those games with PulseAudio as audio server, you will have to follow instructions from [http://nullkey.ath.cx/~stuff/et-sdl-sound/](http://nullkey.ath.cx/~stuff/et-sdl-sound/). Padsp doesn't work with them... No need to try it.

*Warning* Be aware that redirecting library calls to this "wrapper" might be detected as an attempt to cheat. So far PunkBuster? doesn't complain about it but it might in the future. You have been warned!

Setting SDL_AUDIODRIVER="esd" in the wrapper is reported to work better than the default (alsa) 

so only workarounds for now but not really a solution.

ps: sorry to see that you have only small public server.

pps: general seen, an integration of et and ts (or something else) would be cool

---

### Post by Delistone on 2009-06-05
Killing pulseaudio did the trick for me, even with 22khz.
Strange.

---

### Post by jbruced on 2009-06-05
> **Burneddi said:**
> OK as having the same problem and still lacking to find the solution I can't really help, but well:

You probably have a Radeon card. That is the problem.
See, for some reason, 3D acceleration doesn't work at all for some Radeon cards (or the drivers) in 9.04. Seems like the radeon driver and radeon-hd driver are concerned.. Not sure of fglrx.

So, check what driver you're using from /var/log/Xorg.0.log :
```
gedit /Var/log/Xorg.0.log
```
There should be something like
```
(II) LoadModule: "radeon"
```
if you have a Radeon video card. If that is the case, there's pretty much nothing you can do except revert to 8.10 until the bug is fixed. It should work in 8.10 no problem..

+1

Had to install 8.10 for my son, still works great though!

---

