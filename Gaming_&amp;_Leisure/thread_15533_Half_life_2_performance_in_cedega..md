---
title: "Half life 2 performance in cedega."
date: 2005-02-15
forum: Gaming &amp; Leisure
---

### Post by puzzledm on 2005-02-15
I have had half life 2 for a week now and can not seem to get it run at a useable level.  I have been following the instructions on this page [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=60](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=60) but none of it seems applicable to Ubuntu.  

My machine specs are:
Amd Athlon XP 1900+ 
512 ram
Geforce 5600XT 256ram running at 4xagp (I think)
At the moment I can only run it at 800x600 with Everything off!!

I haven't tweaked my XFree86 config file much other than to add 'Renderaccel" to it.  

I was just wondering if anyone has got any ways of checking how well my system should work.  Or how to apply the above tweaks to Ubuntu. Or any other suggestions to get it to work. 

I really want to play this game so any suggestions would be great. :|

---

### Post by dejitarob on 2005-02-15
Eh, you barely could run HL2 in Windows let alone Cedaga. I have similiar specs but an Athlon 2000+ XP and fx5700ultra and it was barely playable in 800x600 for most maps. The singleplayer is worse than the first and multiplayer is boring until possibly more mods are released. Oh yea there's those publicly available hacks that they cannot seem to remedy as well. I'm just happy that ET runs slightly faster than Windows. I would be interested in any performance tweaks for Ubuntu though.

---

### Post by caiphn on 2005-02-15
I ran Hl2 under Windows XP with a 1800+ and a 64meg 8420 ASUS card and it ran fine at 1024x768, everything either turned on or set to medium, this was right after a reformat as well however. (It was crashing on me previous to the reformat)

---

### Post by tkiesel on 2005-02-15
puzzledm,

Did you add the ["NvAGP" option](http://ubuntuguide.org/#enhancenvidiaperformance)  to your XF86Config-4? I think that one turns on AGP support, but I'm honestly not that certain. X configuring is a dark art I have yet to master.

Wishing you luck,
T

---

### Post by valadil on 2005-02-16
Are you using nvidia drivers with GLXy stuffs turned on?  I really should get around to trying out HL2 in cedega.  I got 90 or so frames per second out of it in windows on the stress test.

---

### Post by puzzledm on 2005-02-16
As far as I can see from looking around Windows runs hl2 at a much better rate under the same spec machine compared to running it in Linux.  I am just wondering why?  Surely there should be a way to match the same performance in Cedega.   :roll:  Especially considering most other games I have been playing have been getting a performance boost being played in Linux!

---

### Post by rlwelch on 2005-02-16
I don't think so. I would never expect better performance out of a Linux system in emulating a game compared to running it native on a Windows computer, especially games which are DX9-shader-intensive like Far Cry and Half Life 2. The Linux system will be substantially slower. I know mine is. I've got a Geforce 6800 and I can't keep 40fps at 640*480, DX7 mode, lowest details in Half Life 2 under Linux.

It's only for Linux native games (Quake 3, ET, RTCW, UT2004, Doom 3, among others) that you could ever hope to see comparable performance in.

---

### Post by valadil on 2005-02-17
Some slightly older games (jedi academy for instance) run better in linux for me.  HL2 (tried it out on linux this week) does not.

I imagine opengl games would have a better chance at running well in linux.  DirectX, not so much.

---

### Post by jdodson on 2005-02-17
halflife 2 is rock solid awesome on my rig.  i have a amd 64 3000+ with a gig of ram and a 256M gforce 5700+.  i have no problems with the game under 1024x768 with the options turned up.

there is an optimization on [http://www.ubuntuguide.org](http://www.ubuntuguide.org) that said it would increase performance if you added it to your config.  i found that it dumped my performance into the toilet.  it was [this optimization that was the culprit.](http://www.ubuntuguide.org/#enhancenvidiaperformance)  perhaps turn that off, that might help..... or not, it did for me.

i only run cedega for a few games anyways, war3 and halflife2.  i have neverwinter, ut2004 and enemy territory all native and they run great.  oh i think i installed starcraft, that works fine though i havent played it much.

---

### Post by valadil on 2005-02-17
jdodson:

RenderAccel is easily switched off.  What, if anything, do you use for NVagp?

---

### Post by jdodson on 2005-02-17
[QUOTE=valadil]jdodson:

RenderAccel is easily switched off.  What, if anything, do you use for NVagp?[/QUOTE]

i will check when i get home.  i use the defaults.  the only commands i ran to get 3D working were the following straight from the guide:

```
 
$ sudo apt-get install nvidia-glx
$ sudo apt-get install nvidia-settings
$ sudo nvidia-glx-config enable
```

---

### Post by dejitarob on 2005-02-18
[QUOTE=jdodson]there is an optimization on [http://www.ubuntuguide.org](http://www.ubuntuguide.org) that said it would increase performance if you added it to your config.  i found that it dumped my performance into the toilet.  it was [this optimization that was the culprit.](http://www.ubuntuguide.org/#enhancenvidiaperformance)  perhaps turn that off, that might help..... or not, it did for me.[/QUOTE]In your /etc/X11/XF86Config-4 under the nvidia section try 	
```
Option          "RenderAccel"           "true"
Option 		"NvAGP"			"3"
```The 3 enables hardware agp, 1 is software agp emulation mode I believe. 
[QUOTE=puzzledm]As far as I can see from looking around Windows runs hl2 at a much better rate under the same spec machine compared to running it in Linux.  I am just wondering why?  Surely there should be a way to match the same performance in Cedega.   :roll:  Especially considering most other games I have been playing have been getting a performance boost being played in Linux![/QUOTE]Check out [this article](http://www6.tomshardware.com/howto/20020531/index.html) on tomshardware for benchmarks under linux including with cedaga.

---

### Post by bored2k on 2005-02-20
Performance problems ? ok Linux can b slower, but have y`all tweaking the hl2/hl2/cfg/config.cfg file ? this allows uber performance upgrades  8-) 

also setting higher heapsizes [128000 or higher than default 64k]

Check advanced tweaking here: [http://www.tweakguides.com/HL2_7.html](http://www.tweakguides.com/HL2_7.html) [advanced cfg config applies to all systems, not only Winblows]

---

### Post by Arktis on 2005-02-24
I found a great performance boost for HL2 with cedega. I'm using an nvidia FX 5200 with an athlon xp 2400 and 500 megs of ram. I tried pretty much everything and I was still getting 10-19 frames per second (using cl_showfps in the in-game console to display the fps).

The first thing I noticed was that I needed to stop running hl2 in a window. I got a performance boost of about 10 frames per second just by running in fullscreen. I read around and some people suggested starting hl2 with the parameter -dxlevel 80 or -dxlevel 81 but that actually did nothing. Then I read that for the FX 5200, half-life 2 defaults to hardware direct x version 8. So I ran it with the parameter -dxlevel 90 and lo and behold, I was able to get 25-71 fps at an average of about 30-41! This made the game extremely playable. And to me, it's indistinguishable from running it on windows.

This tweak will probably work for a few different cards besides the 5200 because as I understand it, in the FX series they used basicly the same chipset for a few different versions.

Make sure after you add the parameter, when you launch the game go to the advanced video dialog and set everything to the lowest setting to get the best performance (hl2 will turn everything to medium or reccomended settings when you first launch with the dxlevel 90 parameter).  Both hardware and software direct x level should read as 9 in this dialog.

---

### Post by rlwelch on 2005-02-26
Rrrr... My HL2 won't start in DX9 mode in Ubuntu: it crashes.

---

### Post by puzzledm on 2005-02-27
I added -dxlevel 90 to my launch options and it crashed so I had to hit ctrl-alt-bckspc and restart x except now Gnome won't start - does anyone know how I can get it back on??

---

### Post by Dylanby on 2005-02-27
Try a complete reboot & see what happens.

---

### Post by Snipersnest on 2005-02-28
Current DX 9 support isn't really there in Cedega...shorta, but its pretty fake. 

You best bet is to add -dxlevel 80 to your launch options in CS:S. 

I'm not getting that great of FPS with my high dollar card either. If anyone else knows some tricks I should do let me know.

Ubuntu 5.04
AMD 2600+ barton
1GB PC2700
250GB HD
Geforce 6800 GT OC
SB Live! X Gamer
Cedega 4.2.1/P2P 1.3.2 (Subscribed)

---

### Post by Arktis on 2005-02-28
> Current DX 9 support isn't really there in Cedega...shorta, but its pretty fake.

Strange.  Works better for me than the dx 8 support.  It's the only thing that makes hl2 bearable. :-|

---

### Post by cmsj on 2005-03-01
[QUOTE=rlwelch]emulating a game[/QUOTE]

WINE Is Not an Emulator ;)

It's slower because Microsoft have a load of people working on Windows's DirectX, Transgaming doesn't. As they spend more time improving the code paths in cedega's DirectX then the games will improve.

---

### Post by cmsj on 2005-03-01
[QUOTE=dejitarob]1 is software agp emulation mode I believe. [/QUOTE]

huh?! noooo.

Read NVIDIA's README file (in the driver packages or on their website). The different values for NvAGP specify what AGP driver to use, either the agpgart drivers in the kernel, the drivers NVIDIA has included in their X driver or no AGP support.

---

