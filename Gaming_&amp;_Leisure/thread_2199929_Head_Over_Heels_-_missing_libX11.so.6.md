---
title: "Head Over Heels - missing libX11.so.6 ?"
date: 2014-01-16
forum: Gaming &amp; Leisure
---

### Post by Carl H on 2014-01-16
I've just installed the Linux remake of Head Over Heels (all-time classic ZX Spectrum game) from here [http://retrospec.sgn.net/games/hoh/](http://retrospec.sgn.net/games/hoh/)

It's about 10 years old now, and I've previously installed it on loads of Linux distros over the years with no problem.

However, on my 64 bit Xubuntu 13.04, when I try to run it I get this error (HoH is the executable that the startup script runs) :- ** ./HoH: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory **

A quick search on the net shows that libX11.so.6 is in the package libX11-6, however **apt-get install libX11-6** returns with **libx11-6 is already the newest version**. 

So I already have the library that's missing - I've found it in /usr/lib/x86_64-linux-gnu 

What do I need to do?

---

### Post by mastablasta on 2014-01-17
is the game compiled for 64bit? if not then you need libraries to run 32bit programmes.: [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

i didn't know they've made these for linux. i need to check them out.

---

### Post by kostkon on 2014-01-17
> **Carl H said:**
> A quick search on the net shows that libX11.so.6 is in the package libX11-6, however **apt-get install libX11-6** returns with **libx11-6 is already the newest version**.
Try like that to get the 32bit version:
```
sudo apt-get install libx11-6:i386
```

---

### Post by Carl H on 2014-01-17
> **kostkon said:**
> Try like that to get the 32bit version:
```
sudo apt-get install libx11-6:i386
```

That's got it working, thank you!  Unfortunately, there's no sound.... it was made in the days of OSS, and doesn't work with ALSA. Don't suppose there's any way to add OSS, is there? 

BTW, this is by no means the first 64 bit distro I've played this game on, and none of the others needed 32 bit libraries installing. I've just checked on my Debian 7.3 box and the i386 libraries are there already. Must be an new-ish Ubuntu thing to remove them?

---

### Post by kostkon on 2014-01-17
> **Carl H said:**
> That's got it working, thank you!  Unfortunately, there's no sound.... it was made in the days of OSS, and doesn't work with ALSA. Don't suppose there's any way to add OSS, is there?
Actually, there is. PulseAudio provides a utility that can "emulate" OSS for you, just run the game like this:
```
padsp game_executable
```

---

### Post by Carl H on 2014-01-17
So close, but ...

[B]ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/pulseaudio/libpulsedsp.so' from LD_PRELOAD cannot be preloaded: ignored.
Failed to initialise sound driver!
Insufficient digital voices available[/B]

:(

---

### Post by Carl H on 2014-01-18
```
sudo apt-get install pulseaudio-utils:i386 osspd:i386
```

This crashed and raised an error report, but running the game through padsp does produce sound now. The game sound effects seem more or less alright but the background music is a bit odd. 

Thanks for your help, kostkon.

---

### Post by folgers on 2014-02-01
I enjoy the game Head Over Heals too. Make sure you have alsa-oss installed, then start the game with aoss.
aoss hoh

---

