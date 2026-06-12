---
title: "Games do not work"
date: 2007-06-03
forum: Gaming &amp; Leisure
---

### Post by drumjunky on 2007-06-03
I just installed Frets on Fire and Nexuis and every time I try to load any of them, a screen pops up and flashes about a dozen times and then goes away. It seems like it wants to load but something is tweaked.:confused: I have Ubuntu Studio. I don't know if that has anything to do with it. Anybody else with a similar problem?

---

### Post by hikaricore on 2007-06-03
Launch them from a terminal and watch for errors?

Also posting your hardware (especially video hardware) and what drivers you have installed for said hardware might help someone help you.

---

### Post by drumjunky on 2007-06-03
I'm running an AMD Athlon 2400 or 2600, not sure which. Video card is Nvidia Asylum GeForce. Here's what the terminal says:

drumjunky@ubuntu:~$ nexuiz
Console initialized.
Nexuiz Linux 23:49:57 Feb  7 2007
Trying to load library... "libz.so.1" - loaded.
Compressed files support enabled
Added packfile /usr/share/games/nexuiz/data/data20070123.pk3 (2875 files)
Trying to load library... "libcurl.so.3" - loaded.
cURL support enabled
Initializing client
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Ogg Vorbis support enabled
couldn't exec config.cfg
couldn't exec data/campaign.cfg
couldn't exec autoexec.cfg
Starting video system
Video: fullscreen 800x600x32x60hz
Linked against SDL version 1.2.11
Using SDL library version 1.2.11
Failed to set video mode to 800x600: Couldn't find matching GLX visual
Desired video mode fail, trying fallbacks...
Video: fullscreen 800x600x32x60hz
Linked against SDL version 1.2.11
Using SDL library version 1.2.11
Failed to set video mode to 800x600: Couldn't find matching GLX visual
Video: fullscreen 800x600x16x60hz
Linked against SDL version 1.2.11
Using SDL library version 1.2.11
Failed to set video mode to 800x600: Couldn't find matching GLX visual
Video: fullscreen 640x480x16x60hz
Linked against SDL version 1.2.11
Using SDL library version 1.2.11
Failed to set video mode to 640x480: Couldn't find matching GLX visual
Video: window 640x480x16x60hz
Linked against SDL version 1.2.11
Using SDL library version 1.2.11
Failed to set video mode to 640x480: Couldn't find matching GLX visual
Quake Error: Video modes failed

Any ideas as to what may be causing this?

---

### Post by Feba on 2007-06-03
Are you using feisty? Go to system -> administration -> restricted drivers manager, and make sure it's on.

You might also have to edit your xconfig crap, I forget how to do it, but it's pasted in about one in five threads in the Absolute Beginner Forum.

---

### Post by Feba on 2007-06-03
```
sudo dpkg-reconfigure xserver-xorg
```
run that. Use spacebar to select things. let us know how it goes

---

### Post by drumjunky on 2007-06-04
The problem turned out to be that my restricted drivers manager had the video drivers turned off. After that it was cake. Doh! 
One thing Ubuntu teaches is patience. ;)

---

### Post by Feba on 2007-06-04
You know, I just noticed that the title of this thread is really obvious ;) "Of course they don't "work"!"

Glad to help :D

---

