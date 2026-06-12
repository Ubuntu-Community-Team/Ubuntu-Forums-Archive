---
title: "[ N64 ]  How much are you happy of Mupen64 ?"
date: 2006-08-08
forum: Gaming &amp; Leisure
---

### Post by patrick295767 on 2006-08-08
Hi, 

I am playing N64 emu. The games are really very good in N64. 
  
Most of the games are working.
  
I recently tried the Zelda game (high time), and I am getting some problems with colors. And the text is not displayed perfectly. Several roms are giving same results.
  
After using/ trying with other games, I still have impression that mupen64 is kind of buggy still & the plugins not totally 100% perfect yet.
In Windoze the emulation works almost perfect. 
  
That 's kind of a comparison with dgen & hatari & mame that are really working wihtout any single problem.
  
Cheers !!

---

### Post by searayman on 2006-08-08
i couldnt get any games to work in mupen64 in Zelda Ocarina of tiem it said no control connected and woulnt let me use the keyboard! ALso other gaems just were black, like gauntlet legends. If anyone knows how to get guantlet workign please let me know!!!

---

### Post by Frem on 2006-08-08
I'm not very happy at all. Maybe I'm just not using the right graphics plugins with it, but either the games are too slow, or they have major graphical glitches, or the sound dosen't sync, or else the whole thing just crashes.

I've had a bit of luck with Super Smash Brothers and a bit less luck with Super Mario 64, but I can't get much else to work correctly.

---

### Post by patrick295767 on 2006-08-09
> **searayman said:**
> i couldnt get any games to work in mupen64 in Zelda Ocarina of tiem it said no control connected and woulnt let me use the keyboard! ALso other gaems just were black, like gauntlet legends. If anyone knows how to get guantlet workign please let me know!!!

( In Option/configuration of controls:
For the controls, the first plugin is give me the pad workign.
For the keyboard, I use the second plugin gives me the keyboard:
enter = start
and s d ... sthg )
For me, that works 

but indeed colors problems.
  
Concerning Super Mario 64, try this game to setup your Mupen64. It have impression that mupen64 has been programed and tested with this game mainly, as you can see: [http://mupen64.emulation64.com/shots.htm](http://mupen64.emulation64.com/shots.htm)
  
dgen and hatari are working soo well; and its oonly with command line
  
Look how lucky are the windoze users : [http://www.zophar.net/n64.html](http://www.zophar.net/n64.html)

---

### Post by patrick295767 on 2006-08-09
> **searayman said:**
> i couldnt get any games to work in mupen64 in Zelda Ocarina of tiem it said no control connected and woulnt let me use the keyboard! ALso other gaems just were black, like gauntlet legends. If anyone knows how to get guantlet workign please let me know!!!

 News: 

**I invite you to feed thsi thread here with your mupen64 problesm !!**
: [http://www.emutalk.net/showthread.php?t=36971](http://www.emutalk.net/showthread.php?t=36971)
  

Cheers

---

### Post by searayman on 2006-08-09
I need help with guantlet legends an muppen

---

### Post by patrick295767 on 2006-08-09
> **searayman said:**
> I need help with guantlet legends an muppen

Feed maybe the post there with your problems : [http://www.emutalk.net/showthread.php?t=36971](http://www.emutalk.net/showthread.php?t=36971)
 
(I too have some games to have fully working 100% )

---

### Post by Corey4666 on 2006-08-09
is mupen the only linux n64 emulator? cuz in windows all emulators i use work very well includeing playstation 1 i got final fantasy 7, 8, 9 working well and breath of fire etc
is there a ps1 emulator for linux that works good? i been wanting to switch to linux and uninstall windows dual boot but there is so many things i would have to leave behind for gaming ](*,)

---

### Post by simukas on 2006-08-09
muopen is good but i really disapointed in the speed. i could get my 200mgz 32ram old ati 3d rage card pc run mario64 ar full speed with Corn, but i can't make a much better pc  run games at full speed even without sound and low resolution

---

### Post by patrick295767 on 2006-08-10
> **simukas said:**
> muopen is good but i really disapointed in the speed. i could get my 200mgz 32ram old ati 3d rage card pc run mario64 ar full speed with Corn, but i can't make a much better pc  run games at full speed even without sound and low resolution
  
I started a thread in emutalk
Post maybe there too your problems !!
  
Thank you & let's hope taht we'll soon be ready to enjoy N64 gamiign as with dgen/sega or command line based others 

i had too problems wiht making installed the ultra hle for n64 :-(

---

### Post by searayman on 2006-08-10
you keep referign us to your other thread why cant you help us here? There dosent seem to be much going on on your other thread.

---

### Post by play0r on 2006-08-10
heres a mirror of my post on emutalk:

> Re:
Mupen64 works considerablely well considering my boxes specs:
Distro: Ubuntu 6.06 LTS aka Dapper Drake (2.6.17.8 kernel)
CPU: 11000mHz AMD
RAM: 768MB PC133
GPU: 64MB ATI Radeon 7000 Series

these are the plugins i use (and really the only ones that really work proper under my current setup):
GFX: Glide64 v0.7 SP8
Audio: dummy audio plugin (sucks that i have no sound, but prevents sync related lagging)
Input: blight's SDL input plugin 0.0.10
RSP: Hacktarus/Azimer hle rsp plugin

here's my device section from /etc/X11/xorg.conf:
Section "Device"
Identifier "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
Driver "radeon"
BusID "PCI:1:0:0"
VideoRam 65536
Option "RenderAccel" "true"
Option "AGPMode" "4"
Option "AGPFastWrite" "on"
EndSection

my issues with mupen64 seem to be CPU/GPU related (some confirmation of that would be nice, so i can quit second guessing myself lol). mupen64 eats up a massive ammount of CPU resources during emulation in both gui & no_gui modes (which is not supprizing imho, but it's leading to slight problems), so for instance when i play MP3's with XMMS i get a slight drop in FPS (2-5 FPS, sometimes more depending on the game). i have direct rendering enabled according to glxinfo, but i'm sure with that GPU a lot of it could be resolved by moving to a Nvidia card. especially since ATI support in linux is seriously lacking.
but if anyone has any pointers & or tips that may help clear up some of the FPS loss via plugin setup or even my device section in xorg.conf, it would be much appreciated!
also, if someone has some x86 deb packages (for both gui & no_gui) that jive with ubuntu's package setup that'd be supercool.

ez,
play0r

---

### Post by patrick295767 on 2006-08-10
thx !
  
taht's too the mirror of mine> The colors in Zelda arenn't displayed correctly ; they are red sky.

Concerning the Mario64, I observed that with my Xfree86 & 2000Ghz is not enough to have sound in good synchro with the video. It's like there is lags. The ppracer is working fine & glxgears too. Ati rage all in wonder card.

On other PC, it's fine because they are really big cpu.

I have very often the programs that crash
when trying to use the Game pad. On this same pc, no gamepad is made possible. 
  
I hope that emulation N64 will be sooner or later faster than Windoze !! :rolleyes: :rolleyes: :rolleyes:

---

### Post by simukas on 2006-08-10
i hope that too. it get's really anoying that you have to use windoze for a freaky '96 game....

---

### Post by eqisow on 2006-08-11
Mupen64 works great for me, the only game that doesn't really work is Goldeneye. I'm not why you guys are having problems. Are you all using one of the OpenGL graphics plugins?

---

### Post by patrick295767 on 2006-08-11
> **eqisow said:**
> Mupen64 works great for me, the only game that doesn't really work is Goldeneye. I'm not why you guys are having problems. Are you all using one of the OpenGL graphics plugins?

It's wokring for me too, but only one old pc is having troubles for me. 
 
Besides, zelda rom is giving me on all machines troubesl with colors & text. 
  
Which plugins are you using ? video / audio / pad & true emulation optiosn ? 

Thnak you ! 
 
Damn, N64 was really great console box at that time ! I recall. 
The games are still good even though now.

---

### Post by eqisow on 2006-08-11
Right now I'm using TR64 OpenGL, JttL's SDL, blight's SDL input, and Hacktarux/Azimer hle rsp. However, I sometimes switch between TR64 and glN64 depending on the game. Also, I use Dynamic Recompiler under the Mupen64 options.

---

### Post by patrick295767 on 2006-08-11
> **eqisow said:**
> Right now I'm using TR64 OpenGL, JttL's SDL, blight's SDL input, and Hacktarux/Azimer hle rsp. However, I sometimes switch between TR64 and glN64 depending on the game. Also, I use Dynamic Recompiler under the Mupen64 options.

Thank you !!

---

### Post by crhylove on 2007-03-29
How do you install Mupen in Feisty?  It's not in synaptic, I can't find a .deb, and the people at emutalk are all richard-heads.  Thanks in advance.

rhY

---

