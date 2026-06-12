---
title: "Grid Wars keeps crashing Ubuntu"
date: 2007-08-21
forum: Gaming &amp; Leisure
---

### Post by evilkeo on 2007-08-21
Sorry, trying to learn this linux thing. I've downloaded and unpacked Grid Wars 2 for linux and when I double click the gridwars icon, the screen goes blank, then shows some garbage, then brings up the log on screen. I keep reading that Grid Wars works great on Ubuntu, but can't seem to get it to work myself. Please help!

---

### Post by evilkeo on 2007-08-21
sorry, i'm using fiesty fawn. i installed all the updates that i could.

---

### Post by Ek0nomik on 2007-08-21
Where did you download Grid Wars from?

My only guess is that you don't have your video card drivers setup, or you are missing dependencies (library files) that are required to play the game.

---

### Post by evilkeo on 2007-08-22
[http://gridwars.marune.de/](http://gridwars.marune.de/)

you're probably right about the dependencies. all i've done so far is get fiesty fawn installed and get xmame running. and that alone took me 2 days, heh. i'm trying to learn as i go. all i knew about linux beforehand was some basic commands from a computer science class.

i did just play with some of the built in screen savers and previewing the screen saver crashed in the same fashion that grid wars did.

---

### Post by Ek0nomik on 2007-08-22
This looks like you will definitely need your video card drivers working properly.

Do you have an ATI or nVidia card?  Did you install drivers for both of those cards?

---

### Post by Ek0nomik on 2007-08-22
Wow.  I just downloaded and ran that.  That's a pretty fun game.  :)

---

### Post by charlieg on 2007-08-22
Do you have desktop effects enabled?  Compiz (the window manager behind desktop effects) and games don't always play nicely together.

---

### Post by evilkeo on 2007-08-23
no, desktop effect aren't on. i've only had the computer up and running for a few days now, just enough to kind of learn my way around and get mame working, heh.

---

### Post by Tuna-Fish on 2007-08-23
try and drop this to the terminal:
```

glxinfo |grep direct

```

if you have video drivers set up correctly for direct rendering, it should answer:
```

direct rendering: Yes

```

If not, try checking the restricted drivers manager from the system management menu.

---

### Post by evilkeo on 2007-08-23
mine says:
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

Restricted Drivers says I don't need anything.

I'm not even sure what drivers I need for my computer. It's an old Compaq I had a bunch of sitting in the garage. Deskpro Slim line something or other- Pentium III, somewhere around 4-500 mhz.

---

### Post by evilkeo on 2007-08-23
sorry, i thought i mentioned that i was running onboard video.

---

### Post by evilkeo on 2007-08-25
any ideas?

---

### Post by Tuna-Fish on 2007-08-25
Do you even know if it has a opengl-supporting graphics card?

---

### Post by arfink on 2007-10-16
I know the post is a little old, but I just got this working today. You NEED to have OpenGL acceleration to run this game. Also, the sound effects run fine in ALSA, but the music does not. I think the music is trying to be played by the BASS plugin, which I believe only supports OSS right now. Other than that, it works marvellous. But, yes, you absolutely must have a 3d accelerator to run this game.

---

### Post by zorkerz on 2009-01-25
Just installed this game in ubuntu 8.10 x86-64 and am experiencing the same crash. Screen goes blank and then logged out. 

Did anyone ever find a solution to this?

I have suspicions it is related to the current linux drivers for my intel x3100 card using the GMA965 chipset.

---

### Post by phantom3113 on 2009-05-31
I've just downloaded this and installed this as well (on 8.10 i386) and have similar issues. It loads up, but the menu page is a garbled mess (lines everywhere, like it was stretched and stripped) and it doesn't kick me out. However, I have to restart X to get out of it, so it might as well make me log back in :P. I blame ATI and their poor linux support :(

---

