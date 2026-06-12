---
title: "Tutorial: Wolfenstein: Enemy Territory with PulseAudio"
date: 2008-09-12
forum: Gaming &amp; Leisure
---

### Post by Bios Element on 2008-09-12
To get ET to work with PulseAudio, First install it off Playdeb.net.

Then follow the guide located [http://nullkey.ath.cx/~stuff/et-sdl-sound/](http://nullkey.ath.cx/~stuff/et-sdl-sound/) to set it up for sdl sound. But edit the et-sdl-sound.so File.

Change 
```

# SDL audio driver
SDL_AUDIODRIVER="alsa"

```
To This
```

# SDL audio driver
SDL_AUDIODRIVER="pulse"

```

And your set!

---

### Post by devilscemo on 2009-04-21
hi I did all you said but when i launch the game from et-sdl-sound and it doesn't work :(... what should I do??
O btw what do you mean by the et-sdl-sound.so? do you mean the exectuable one?
I have ubuntu 8.04 if that helps...

---

### Post by bruno.vitorino on 2009-05-24
The pulse hack doesn't work, but the alsa does, so I'm sticking with alsa.

---

### Post by charlieg on 2009-09-27
For me (on Fedora) the sound quality with this/ALSA was awful.

The fix was to set the SDL_AUDIODRIVER to "pulse" in et-sdl-sound:

```
# SDL audio driver
SDL_AUDIODRIVER="pulse"
```

---

### Post by wyrless2002 on 2010-01-03
Thanks!

---

