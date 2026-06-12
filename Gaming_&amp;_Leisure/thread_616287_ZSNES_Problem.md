---
title: "ZSNES Problem"
date: 2007-11-18
forum: Gaming &amp; Leisure
---

### Post by Zaiden on 2007-11-18
I'm having an issue with ZNES. After I recieved it from the command "sudo apt-get install zsnes", I tried a few games out, and every game had skipping and staticy sound. Can anyone help me with this?

---

### Post by ddrichardson on 2007-11-18
What are your system specs?

---

### Post by Zaiden on 2007-11-18
From my memory:

Intel Celeron D 2.4ghz
512MB RAM
nvidia FX5200 128MB PCI

---

### Post by Steveway on 2007-11-18
Play around with the sound-settings.
Set the bitrate lower to something like 22150 or so till the sound sounds normal.
This worked for me.

---

### Post by ddrichardson on 2007-11-18
The problem with emulation is that it needs powerful hardware. What it boils down to is that you cannot run Super NES programs on a PC so you need to develop a system that can communicate with PC hardware yet act as the original system intended.

So you create a virtual machine, and these take resources. Unfortunately, sound is *really* intensive. So Zsnes will chop it - to give the framerate priority as the speed the game runs at has a higher priority than the sound.

You can lower the sound rate to 11kHz and that should help, but ultimately the Celeron's lack of cache will cause problems.

---

### Post by NightCrawler03X on 2007-11-18
I often had crackling sound with zsnes myself.

Try setting the bitrate in the sound options to "48000" hz, worked for me.

---

### Post by Marrshu on 2007-11-18
Try installing "libsdl1.2debian-all"   That fixed it for me.

I doubt it's your processor... ZSNES can/should run fullspeed on a Pentium 2.

---

### Post by BigSilly on 2007-11-18
I usually always have this problem with ZSNES, and I have to install libsdl1.2debian-oss from the repository. It removes libsdl1.2debian-alsa, but that's never caused any further problem for me.

---

### Post by dfreer on 2007-11-18
Also, if you are using gutsy and have version zsnes 1.51, you should be able to use libao which solves most sound issues for me.
```
zsnes -ad oss
```
If that doesn't work, you can always go back to using alsa:
```
zsnes -ad alsa
```

---

### Post by Juco on 2007-11-18
yeah i just got zsnes and i got the same problem.  then i did what marrshu said, and instaled that sdl thing, and now when i run zsnes, it opens, but when i click load, it immediately exits.  how do i change it back?

---

### Post by dfreer on 2007-11-18
To uninstall that program that Marrshu recommended:
```
sudo apt-get remove libsdl1.2debian-all
```

But it's probably better to try to troubleshoot what is making zsnes crash. Try running zsnes from the terminal and see if it gives you an error message when it crashes.

---

### Post by Yfrwlf on 2007-11-22
> **Juco said:**
> yeah i just got zsnes and i got the same problem.  then i did what marrshu said, and instaled that sdl thing, and now when i run zsnes, it opens, but when i click load, it immediately exits.  how do i change it back?

Also try removing your .zsnes folder in your home directory if you can't figure it out, you can save your game saves in it but you can delete the other files, then reload ZSnes and see if it then loads OK.  I've run into some config settings that make so it won't load up and that fixed it.

---

