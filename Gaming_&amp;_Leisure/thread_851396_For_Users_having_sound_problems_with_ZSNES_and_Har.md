---
title: "For Users having sound problems with ZSNES and Hardy"
date: 2008-07-06
forum: Gaming &amp; Leisure
---

### Post by dfreer on 2008-07-06
Hi everyone,

  So after a long period of little/no activity, I started looking into the ZSNES Hardy scene. There's been many, many reports in the forums about users not being able to get sound working at all (or scratchy sound), and several solutions have been posted but it seems people still are confused.

So I did some tests of my own, using a default install of Ubuntu x86 Hardy (actually it's the live CD, same thing). I used Chrono Trigger and Tales of Phantasia to test the "scratchiness" of the sound. Let's start with the "official" package provided in the Universe Repository:

```
sudo apt-get install zsnes
```

Default Install Settings (-ad auto/alsa, 32,000 Hz): Absolutely no sound.
OSS (-ad oss, 32,000 Hz): Absolutely no sound.
SDL (-ad sdl, 32,000 Hz): Constant Buzzing in the background, but sound.
SDL (-ad sdl, 48,000 Hz): Great sound.
SDL with libsdl1.2debian-oss (-ad sdl, 32,000 Hz): Decent sound, very faint slowdowns/hiccups.
SDL with libsdl1.2debian-oss (-ad sdl, 48,000 Hz): Decent sound, but stutters a lot.
SDL with libsdl1.2debian-all (-ad sdl, 32,000 Hz): Constant buzzing, but sound.
SDL with libsdl1.2debian-all (-ad sdl, 48,000 Hz): Great sound.

Please note: You can change the sound driver two ways, either by passing the argument "-ad <sound driver>" **once**, or by changing the configuration file located at ~/.zsnes/zsnesl.cfg.

If you pass the argument to the program, say like this:
```
zsnes -ad sdl
```
SDL gets written to the ~/.zsnes/zsnesl.cfg. So there's no reason to pass "-ad <sound driver>" EVERY time you run zsnes, just the once to change it!

The default is "-ad auto", which automatically determines which one to use. On my system it always picks "alsa".




Ok, now for further tests. This is using Nach's patched version of ZSNES 1.51 that fixes zsnes's broken sound in Hardy. You can download the source code and pre-compiled binaries for this version 1.51b here:
[http://board.zsnes.com/phpBB2/viewtopic.php?p=168959](http://board.zsnes.com/phpBB2/viewtopic.php?p=168959)

I'm going to use the core2 binary, as I have an Intel Core 2 Duo processor.

Default Install Settings (-ad auto/alsa, 32,000 Hz): Great Sound.
Default Install Settings (-ad auto/alsa, 48,000 Hz): Great Sound.
OSS (-ad oss, 32,000 Hz): Great Sound.
OSS (-ad oss, 48,000 Hz): Great Sound.
SDL (-ad sdl, 32,000 Hz): Constant Buzzing in the background, but sound.
SDL (-ad sdl, 48,000 Hz): Great Sound.
SDL with libsdl1.2debian-oss (-ad sdl, 32,000 Hz): Decent sound, very faint slowdowns/hiccups.
SDL with libsdl1.2debian-oss (-ad sdl, 48,000 Hz): Decent sound, but stutters a lot.
SDL with libsdl1.2debian-all (-ad sdl, 32,000 Hz): Constant buzzing, but sound.
SDL with libsdl1.2debian-all (-ad sdl, 48,000 Hz): Great sound.

Hopefully this helps people with their sound problems, whichever route they choose (use 1.51 or 1.51b). And hopefully it stops some of the confusion people have running commands wildly without really knowing what they are doing.


*Note: All of these test were performed with zsnes in a 512x448 window (whatever the default window size is), running on my Intel Core 2 Duo @2.00 Ghz processor with my Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (snd_hda_intel). Video Card is Nvidia GeForce Go 7400 (restricted drivers NOT installed).
You may experience additional sound stutters/errors simply if you are not running the game at full FPS, or have problems with your sound card not related to ZSNES.

---

### Post by FranMichaels on 2008-07-07
This should be stickied. :KS

---

### Post by dfreer on 2008-07-07
Thanks! I just finished playing around with x86_64, same results. The only thing to note with x86_64 is that binaries compiled with --enable-libao (which I always do), you must symbollically link the files in /usr/lib32/ao/plugins-2/ to /usr/lib/ao/plugins-2/, otherwise zsnes will seg fault.

---

### Post by CorryJm on 2008-08-26
I managed to get sound -working- using the tips found here (thanks all!)

however, using (-ad sdl, 48,000 Hz) with hi-quality lowpass, my sound is still scratchy and stuttery.

and other tips?

---

### Post by dfreer on 2008-08-26
> **CorryJm said:**
> I managed to get sound -working- using the tips found here (thanks all!)

however, using (-ad sdl, 48,000 Hz) with hi-quality lowpass, my sound is still scratchy and stuttery.

and other tips?

Have you installed libsdl1.2debian-all, and have you used the newer 1.51b? If that doesn't work, try -ad oss, and try the different sound rates like 32,000 Hz - 48,000 Hz.

---

### Post by tuxxy on 2008-08-26
Why dont try snes9express from the repos, this should provide sound out of the box, also I prefer it to zsnes

---

### Post by grossaffe on 2008-08-26
> **tuxxy said:**
> Why dont try snes9express from the repos, this should provide sound out of the box, also I prefer it to zsnes
I would go with the GTK port of SNES9x.

---

### Post by CorryJm on 2008-08-27
zsnes sound stopped again.

I repeated all of the steps again, but nothing.

wha?

I also just tried installing snes9x.
also no sound.

sound works on videos, amarok, etc.
only area it seems to bum out on is the emulators (playstation emulator sound does not work as well)

edit: restarted, sound is back.  =|

---

### Post by Crafty Kisses on 2008-08-28
Thanks for this, to be honest I've had troubles, but this seems to only semi fixed the problems. Thanks though.

---

### Post by dfreer on 2008-10-27
> **CorryJm said:**
> zsnes sound stopped again.

I repeated all of the steps again, but nothing.

wha?

I also just tried installing snes9x.
also no sound.

sound works on videos, amarok, etc.
only area it seems to bum out on is the emulators (playstation emulator sound does not work as well)

edit: restarted, sound is back.  =|

Could be because of flash, I get a lot of reports about pSX no longer working after playing a flash video, rebooting almost always helps.

---

