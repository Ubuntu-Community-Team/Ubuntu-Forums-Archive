---
title: "Info: Space Trader"
date: 2008-06-14
forum: Gaming &amp; Leisure
---

### Post by Cappy on 2008-06-14
[[IMG]http://www.playspacetrader.com/images/newsite/main_header.jpg[/IMG]]("http://www.playspacetrader.com")

Here's a commercial game I've never heard of before but comes with a Linux port:

> In the far future humanity is ruled by The Ministry of Accounts, an oppressive bureaucracy that tracks, records and taxes every transaction of daily life. From the depths of Red Tape a new breed of marketeer arises to challenge the authority and make a profit: the Space Trader is born!

Space Trader is a fast paced action trading game in full 3D. Players compete to make money by buying and selling commodities, capturing fugitives and collecting stash. Challenge yourself, your friends, and your foes in a bid to become the wealthiest Trader in space!

[http://www.playspacetrader.com/](http://www.playspacetrader.com/)

There is also a linux demo, located here: [http://www.playspacetrader.com/system/SpaceTrader-1.0.8_linux_en-US.run](http://www.playspacetrader.com/system/SpaceTrader-1.0.8_linux_en-US.run)

---

### Post by cogadh on 2008-06-14
Wow a single player game for Linux that actually looks pretty good. I'll definitely be giving the demo a try later (must sleep now...).

---

### Post by Perfect Storm on 2008-06-14
Nice found :guitar:

---

### Post by The Cosmic Hobo on 2008-06-14
Looks pretty spiffy, and the price is incredibly reasonable, too.

---

### Post by Vadi on 2008-06-14
Played the game before, it's kinda fun.

---

### Post by cogadh on 2008-06-14
I've got no sound in the game, it keeps producing this error when I try running it normally:
```
/dev/dsp: Device or resource busy
Could not open /dev/dsp
Sound intialization failed.
```
If I try to specify the sound system by running it with -alsa, -oss or -esd after the command, the error chages to this:
```
Could not mmap dma buffer PROT_WRITE|PROT_READ
trying mmap PROT_WRITE (with associated better compatibility / less performance code)
/dev/dsp: Input/output error
Could not mmap /dev/dsp
Sound intialization failed.
```
I've already confirmed that my user is a part of the "audio" group and sound does work on everything else. Anyone got any ideas?

Oh, and I am using Kubuntu 8.04 (finally upgraded from 7.10).

---

### Post by Cappy on 2008-06-14
Have you tried installing alsa-oss and running it with ```
aoss /path/to/game
```

---

### Post by cogadh on 2008-06-14
Okay, that was a step in the right direction, I now get sound, but it is extremely choppy and full of pops and cracks. Actually, the silence was somewhat better ;)

Any other ideas?

---

### Post by plinydogg on 2008-06-15
I've got a sound problem too. Here's the sound portion of the output when I run this game from the command line:

------ Initializing Sound ------
Could not mmap dma buffer PROT_WRITE|PROT_READ
trying mmap PROT_WRITE (with associated better compatibility / less performance code)
/dev/dsp: Input/output error
Could not mmap /dev/dsp
Sound intialization failed.

---

### Post by billybag on 2008-08-20
i keep running into this problem too with a lot of games.

here is an example from Digital paintball 2

```

 ~/.paintball2 $ ./paintball2

Paintball 2 -- Version 2.0
execing configs/config.cfg
Console initialized.

------- sound initialization -------
LoadLibrary("./snd_oss.so")
dlopen("q2a3d.so") failed: q2a3d.so: cannot open shared object file: No such file or directory
Error loading up q2a3d module.
------------------------------------
------- Loading ref_pbgl.so -------
LoadLibrary("./ref_pbgl.so")
ref_gl version: PB2GL 0.22
Using libGL.so for OpenGL...
Initializing OpenGL display
...setting mode 18: 1280 768
Using XFree86-VidModeExtension Version 2.2
I got 8 bits of red
I got 8 bits of blue
I got 8 bits of green
I got 24 bits of depth
I got 8 bits of alpha
I got 8 bits of stencil
Using hardware gamma
------------------------------------
====== Paintball II Initialized ======

70.85.9.178:27900: vninitresponse
70.85.9.178:27900: vnresponse

------- sound initialization -------
LoadLibrary("./snd_oss.so")
/dev/dsp: Device or resource busy
SNDDMA_Init: Could not open /dev/dsp.

------- sound initialization -------
LoadLibrary("./snd_oss.so")
dlopen("q2a3d.so") failed: q2a3d.so: cannot open shared object file: No such file or directory
Error loading up q2a3d module.
Cmd_AddCommand: play already defined
Cmd_AddCommand: stopsound already defined
Cmd_AddCommand: soundlist already defined
Cmd_AddCommand: soundinfo already defined
------------------------------------
recursive shutdown

```

---

### Post by khormin on 2010-04-13
>< Can't stand opening old threads, but didn't find anything else in relation to it.

Getting issues with Space Trader, and other steam games, run in the latest wine - I get a burst of sound at the start, a burst of sound at the end, and that's it.

*Edit: Helps if I define which games...*

---

### Post by khormin on 2010-04-14
Whelp, fixed it. Turns out that wine sometimes asks for ALSA when it should be looking for Pulse. So I googled and found "winepulse", which after installation now has Space Trader running flawlessly.

Thanks anyway!

---

