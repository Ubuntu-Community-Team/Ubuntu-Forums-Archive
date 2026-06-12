---
title: "nes emulator speed/accuracy trouble"
date: 2008-09-11
forum: Gaming &amp; Leisure
---

### Post by &amp;)ky#)^ on 2008-09-11
I'm having trouble getting any NES emulators to work properly for me.  They all emulate and such, but most do so way too fast.  Faster than accurate.  So far, I've tried iNES, FCEU, Mednafen, Nestopia, and XMESS.  All of them but XMESS emulated far too quickly.  XMESS had other difficulties emulating my games.  I figure since they are all doing the same thing, there must be a common thread.  My computer isn't some crazy-fast rig or anything.  It's a low-end laptop.  So what am I doing wrong or what should I try?

---

### Post by kofrad on 2008-09-11
have you tried zsnes?

---

### Post by &amp;)ky#)^ on 2008-09-11
> **kofrad said:**
> have you tried zsnes?

ZSNES is a SNES emulator, not a NES emulator.

---

### Post by grossaffe on 2008-09-11
> **bluej774 said:**
> ZSNES is a SNES emulator, not a NES emulator.

but dude, SNES is like 3x better than NES!
...
:D

---

### Post by &amp;)ky#)^ on 2008-09-11
> **grossaffe said:**
> but dude, SNES is like 3x better than NES!
...
:D

Sorry.  I prefer NES.  Regardless, the software isn't properly emulating the NES.  I could believe that for most of them, but Nestopia is supposed to be a near-perfect emulation of the NES hardware.  When even it didn't work properly, that's when I figured there must be something else going on.

---

### Post by wingnux on 2008-09-11
Have you tried turning VSYNC on?

---

### Post by disturbedite on 2008-09-11
sorry to burst your bubble bro, but it sounds like you're prolly wrong. nestopia is the most accurate nes emulator there is. if you're having speed problems, it seems likely to be on your end, not nestopia's, unless...

> The PAL NES runs at approx. 50 frames per second, while the NTSC console runs at 60 fps. The NES CPU (which also serves as the sound generator) also runs at a slower clock speed (1.79 MHz NTSC, 1.66 MHz PAL). Some NES games were not adjusted for PAL timing, causing them to run slower and have slightly distorted audio compared with NTSC.but i still think it sounds like it is prolly a problem on your end. here is an example of that problem on windows:

> For some reason DirectX was set to override the applications' refresh rate settings and use 75 Hz instead. By disabling the setting (through DXDiag) Nestopia worked just fine with VSync on even in full screen mode.

This also might account for some of the reports about Nestopia running too fast on some other systems.

so perhaps you're not using the correct refresh rate & using vsync (like mentioned above) or the refresh rate is being overridden somehow so the games run too fast.

but i can't be certain about a lot of things, you seriously skimped on details.
distribution/version/nestopia/version/rom/region would be helpful.

---

### Post by &amp;)ky#)^ on 2008-09-11
I compiled the latest version of Nestopia when I tried it.  It was 1.40 G.  FCEU, Mednafen, and XMESS were all the hardy repo versions.  iNES was the latest version on the website.  All the roms I've tried run too fast.  I've been using all NTSC roms and have set the settings as such.

How do I turn on vsync for Nestopia?  I don't see an option in the GUI and I don't know what command line switches are available.

---

### Post by Mednafen on 2008-09-11
There's probably something wrong with your sound output device, or the driver for it.

---

### Post by &amp;)ky#)^ on 2008-09-12
Why would that affect the speed/accuracy of emulation?

---

### Post by FranMichaels on 2008-09-12
> **bluej774 said:**
> Why would that affect the speed/accuracy of emulation?

Video and audio sync? Seriously, I don't know, but it doesn't hurt to try changing a setting.

In mednafen, edit the config file

```
gedit ~/.mednafen/mednafen.cfg
```
Use find to get these sections, put these values:

;Select sound driver.
sounddriver ALSA

;Select sound output device.
sounddevice sexyal-literal-default

;Select video driver, "opengl" or "sdl".
vdriver 0

;Attempt to synchronize OpenGL page flips to vertical retrace period.
glvsync 0

Now for the above two, I have driconf set to vsync all my opengl stuff overriding individual ettings. Feel free to manually enable glvsync by putting a 1 (I don't recommend not using opengl if you are getting acceleration)

Best of luck!

P.S. Don't use xmess or xmame, they are no longer updated. 
Use sdlmame/sdlmess instead
[http://rbelmont.mameworld.info/?page_id=163](http://rbelmont.mameworld.info/?page_id=163)
Part of the official source trees of mame and mess now too... :D

---

### Post by &amp;)ky#)^ on 2008-09-13
I tried your settings, but there was no change.  I played with the settings a little and I found that if I disable sound be kept "no sound throttling" enabled, it emulated only a little faster than it should have.

Regarding sdlmame and xmame, I still use xmame because I found many of my roms wouldn't play correctly or at all under sdlmame while they'd work fine under xmame.  Any reason that may be?

---

### Post by FranMichaels on 2008-09-13
> **bluej774 said:**
> I tried your settings, but there was no change.  I played with the settings a little and I found that if I disable sound be kept "no sound throttling" enabled, it emulated only a little faster than it should have.

Regarding sdlmame and xmame, I still use xmame because I found many of my roms wouldn't play correctly or at all under sdlmame while they'd work fine under xmame.  Any reason that may be?

I see, at least this sound issue may help you narrow the problem down further. What sound hardware do you have? Does it change if you disable the sound server: go to System -> Preferences -> Sound, click the sound tab and disable software mixing (reboot may be necessary, I don't know if it shuts down the daemon automatically.)

As for the mame roms, they are simply out of date, and likely require a newer dump. This is explained on the official mame dev site faq.

> **I had ROMs that worked with an old version of MAME and now they don't. What happened**?

As time passes, MAME is perfecting the emulation of older games, even when the results aren't immediately obvious to the user. Often times the better emulation requires more data from the original game to operate. Sometimes the data was overlooked, sometimes it simply wasn't feasible to get at it (for instance, chip "decapping" is a technique that only became affordable very recently for people not working in high-end laboratories). In other cases it's much simpler: more sets of a game were dumped and it was decided to change which sets were which version.
[http://mamedev.org/devwiki/index.php/FAQ:ROMs#I_had_ROMs_that_worked_with_an_old_version_of_MAME_and_now_they_don.27t.__What_happened.3F](http://mamedev.org/devwiki/index.php/FAQ:ROMs#I_had_ROMs_that_worked_with_an_old_version_of_MAME_and_now_they_don.27t.__What_happened.3F)

If you have sdlmame installed, and it indeed sees the folder with your roms, pass:
-verifyroms
as a parameter

It will list which sets are good, what is missing, etc.

---

