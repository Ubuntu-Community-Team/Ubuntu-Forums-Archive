---
title: "ZSNES No Sound With Intrepid ALSA and Pulseaudio"
date: 2009-02-14
forum: Gaming &amp; Leisure
---

### Post by jbsmith86 on 2009-02-14
I have ubuntu Intrepid. My sound system consists of ALSA and Pulseaudio using the directions from this forum:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I've tried running ZSNES various ways
installed libsdl1.2debian-all
zsnes -ad pulse
zsnes -ad alsa
zsnes -ad sdl
zsnes -ad oss

tried installing various different versions of libsdl1
tried many different ROM files
tried changing zsnes settings (sample rates etc)
system sound works perfect but I have gotten no sound out of ZSNES whatsoever any ideas?

---

### Post by jbsmith86 on 2009-02-14
bump

---

### Post by Woojoo//.deb on 2009-02-15
i had the same problem 1 day ago
i solved it with downloading the 1.50b version which you need to build yourself with SDL support then its works for ALSA as far as i had understood ^^

the one that i had build runs smooth and sings like a bird ^^



edit:
i made a .deb of my build please notice USE AT OWN RISK

bamn.de/downloads/zsnes_1.51b-0_i386.deb

---

### Post by doorknob60 on 2009-02-15
[http://www.snes9x.com/phpbb2/viewtopic.php?t=3703](http://www.snes9x.com/phpbb2/viewtopic.php?t=3703) Try that, works well, nice GTK GUI, and better sound support.

---

### Post by jbsmith86 on 2009-02-17
tried the .deb and the snes9x gtk port and still no sound.
i'm surprised the zsnes pulse driver does nothing

---

### Post by Woojoo//.deb on 2009-02-20
im not a master at linux but it could be that you need the sdl lib files to get it running try getting the "libsdl1.2debian-all" package if you dont have it. that package normaly as far as i understand supplys the generel support for sdl to use pulse and alsa 

if that doesnt work i dont know ^^


but did you try the apendics C of that howto you posted above?

i didnt read it complete but there seems to be an problem solving solution for applications which dont go well on pulse

---

