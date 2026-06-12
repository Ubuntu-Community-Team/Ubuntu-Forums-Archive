---
title: "Snes9x"
date: 2006-11-13
forum: Gaming &amp; Leisure
---

### Post by rikguenther on 2006-11-13
how can i get snes9x to work on my linux machine?  every one that ive tried to download when it goes to extract it says incompatible. 

so, i go to the repositories for help, and sure enough i find it, download and install.. but then i cant find it.  i do a search on the entire file system, and all i can find are icons for it and some .desktop files.  i went to the terminal and typed in every variation i could think of for snes9x and still came up with nothing.  so if anyone else has had this problem before and knows how to fix it or even has any advice (different distros of a snes emulator) then ill gladly accept.

---

### Post by DarkN00b on 2006-11-13
Get the frontend from the repositories. It is called 'Gsnes' I think. Snes9x for linux is a command line only app so unless you want to mess around inputting long lines of code at the cli, you'd do well to get the frontend. It can save all the options you want for each individual game, as well as having a cheat code database if you want to use codes. One thing about GSnes is that you will need to adjust the sound properties if you want good sound.

---

### Post by rikguenther on 2006-11-14
ok so now ive got snes9x to work in the terminal.  i just type

snes9x /home/rik/rom.smc 

and it works, but im still having problems.

1) no sound.  it says in the terminal that it cant configure the sound or something (im not at my linux box right now.) 

2) framerate is crap. it like skips around and whatnot.

3) fullscreen. id like it to go into full screen but if not then im ok with windowed mode.

---

### Post by kessaris on 2008-09-14
You really gotta download the front end mate.

do a search for snes in the package manager, you'll see at least two frontends for snes9x

---

### Post by grossaffe on 2008-09-16
> **kessaris said:**
> You really gotta download the front end mate.

do a search for snes in the package manager, you'll see at least two frontends for snes9x

I prefer the GTK port of snes9x

---

### Post by sackbj on 2008-10-23
I'm digging up this thread rather than starting a new one.

I have been playing several games using Snex9x.  Most notably, I am a good way into Earthbound.  I did all this on my Vista computer and now my main productivity computer will run Ubuntu.  I would like to somehow backup the save states and transfer them to Ubuntu.

Is there any way to maintain the save states from the Windows Snes9x to the Ubuntu version?  If there isn't any way to do that, can I use Earthbound's regular save function and just transfer the ROM file?

---

### Post by FranMichaels on 2008-10-23
If it's the same version of snes9x, the save state should work fine, at least this holds true for zsnes. The actual save ram data (in game saving) is universal, you could even dump it onto a cart and play it on a super nintendo. 
Look for a .srm file and just copy it over.

---

