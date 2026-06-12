---
title: "White noise with SDLMAME"
date: 2010-08-10
forum: Gaming &amp; Leisure
---

### Post by kakyoism on 2010-08-10
I'm with SDLMAME 0.136. 
The sound would initially stay normal for a couple minutes.
then at certain points the audio just burst into a load of whitenoise and nothing else, no FX or music at all.
I doubt that this is underrun or overrun, because however I set the audio buffer in mame.ini (1, or 2, or 3, etc), the noise will show up still.

Any ideas?

---

### Post by kakyoism on 2010-08-10
bump

---

### Post by DoktorSeven on 2010-08-10
Which game or games is this?  New, old, both, any?

When you launch the game, does it say there are problems with the audio emulation for that game?

What are your hardware specs?

---

### Post by BigSilly on 2010-08-10
I think I may have had this before, but I'm not sure. You could try running ```
sdlmame -ad sdl
``` from a terminal and see if that solves it. If I remember correctly, when I did that you got the white noise for a moment or two, then it subsides never to be heard again. You can run your MAME as usual after that. You don't have to input the terminal codes again.

Unless I'm completely on the wrong track.

---

### Post by kakyoism on 2010-08-10
@DoktorSeven

1. Any game.
2. No
3. Audio hardware should be on-board AC97.

---

### Post by kakyoism on 2010-08-10
@BigSilly

I'll try this!

---

### Post by kakyoism on 2010-08-10
@BigSilly

I tried your suggestion but it doesn't work. After a while it still happens.
I found that the most common scenario is when I resume a paused game. 

I also noticed among the terminal log info, there is this when the noise arise:
```
Sound buffer: overflows=1 underflows=5
```

So does this say it's really just overrun and underrun problem??

---

### Post by kakyoism on 2010-08-15
bump,

---

### Post by kakyoism on 2010-08-15
seemed to be solved by setting in mame.ini
```
audio_latency 4 
```

---

