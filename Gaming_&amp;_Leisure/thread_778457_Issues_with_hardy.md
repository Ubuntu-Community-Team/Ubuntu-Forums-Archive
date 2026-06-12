---
title: "Issues with hardy"
date: 2008-05-02
forum: Gaming &amp; Leisure
---

### Post by fatalGlory on 2008-05-02
Since i wiped my feisty install and installed hardy, I've had a few different problems with games now and I'm wondering if they are all traceable to some root issue - or if there is any advice out there on any of the following:

**Frets on Fire:** can't play a song or quit the game, screen goes red and game hangs - have to restart X.

**Mupen64:** With different video plugins, can only get about 4fps - unplayable and highly irritating.

**XMAME:** Slow framerates and keyboard response in games.  Hangs when I press escape to exit

Anyone have any ideas?  My initial reaction is some video driver issue in hardy.  I have nvidia's binary driver version 169.12 installed from the nvidia website.  glxgears gives me about 12,000 frames so I know I have the drivers working properly for direct rendering.  Please help.  I wanna be able to play all these games again.

---

### Post by Tomatz on 2008-05-02
> **fatalGlory said:**
> Since i wiped my feisty install and installed hardy, I've had a few different problems with games now and I'm wondering if they are all traceable to some root issue - or if there is any advice out there on any of the following:

**Frets on Fire:** can't play a song or quit the game, screen goes red and game hangs - have to restart X.

**Mupen64:** With different video plugins, can only get about 4fps - unplayable and highly irritating.

**XMAME:** Slow framerates and keyboard response in games.  Hangs when I press escape to exit



Anyone have any ideas?  My initial reaction is some video driver issue in hardy.  I have nvidia's binary driver version 169.12 installed from the nvidia website.  glxgears gives me about 12,000 frames so I know I have the drivers working properly for direct rendering.  Please help.  I wanna be able to play all these games again.


Are you sure compiz isn't enabled?

---

### Post by fatalGlory on 2008-05-02
What would that do?  And exactly what do you mean?  I have compiz fusion installed (its the default) but I usually switch back to metacity with the compiz-fusion icon (it has a "select window manager" option).

---

### Post by jnuz on 2008-05-02
for FoF, try my binary posted in another thread. there are slow down issues associated withpy-opengl3, so most of us are using version 2 from the feisty repo. my binary should be universal though and not have any dependency issues. just use your song folder

[http://ubuntuforums.org/showthread.php?t=777060](http://ubuntuforums.org/showthread.php?t=777060)

---

### Post by fatalGlory on 2008-05-02
Thanks dude, downloadin it now.  Still don't know about the emulators though.  Guess its probably unrelated since heaps of other openGL games are running fine (ut2004, Warcraft 3 in wine, etc.)

---

### Post by fatalGlory on 2008-05-02
That binary didn't change anything.  Cool interface, but the no song playing or exiting issue remains.  Thanks anyway.

---

### Post by fatalGlory on 2008-05-02
After doing:
```
sudo apt-get install libsdl1.2debian-pulseaudio
```

**Mupen64** works perfectly again (although my testing was pretty quick)

**XMame** has sound again (but a bit choppy) and I can exit cleanly.  Framerate is almost all good, any lag is probably due to video/audio syncing or whatever setting is causing audio to be choppy.  Still - very nearly works how its meant to, probably very small tweaks required.

**Frets on Fire** I got to run and play a song by going into nvidia-settings and turning off sync-to-vblank in the "X Server XVideo Settings" section.  Then after installing the sdl-pulseaudio package above, it crashes to the desktop at low res and no mouse control when I try to play a song.  Still couldn't quit cleanly in either scenario.

SDL, hardy and pulseaudio seem to be having some teething problems.  Here's hoping they get patched quickly.  Until then, at least I can play Lylat Wars with my Wii Remote again :)

---

### Post by fatalGlory on 2008-05-07
Woke up this morning, for no reason at all, tried to launch vanilla Frets on Fire from the Hardy repos again and it worked fine!

There have been a couple of automatic updates since my previous post so I'm assuming one of them fixed it - no idea which one though.  Mad props to the Ubuntu Devs for fixing it so quickly (whatever it was).

Happy rockin!

---

