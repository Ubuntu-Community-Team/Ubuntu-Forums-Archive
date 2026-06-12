---
title: "Fretsonfore Doesn't Run"
date: 2007-12-15
forum: Gaming &amp; Leisure
---

### Post by Chris Riley on 2007-12-15
I'm running Gutsy 64 bit on an AMD 64 x2. Want to try some of the interesting new programmes that I previously haven't been able to afford (M$).

I've installed Fretsonfire from the repository, but when I run it from the menu, I get a black screen momentarily, then the screen returns to desktop.

When I run from terminal, I get the script below. Trouble is, this is gobbledygook to me.

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 166, in __init__
    self.svg = SvgContext(geometry)
  File "/usr/share/games/fretsonfire/game/Svg.py", line 78, in __init__
    self.setGeometry(geometry)
  File "/usr/share/games/fretsonfire/game/Svg.py", line 91, in setGeometry
    geometry[2], geometry[3])
  File "/usr/share/games/fretsonfire/game/DummyAmanith.py", line 42, in SetViewport
    glViewport(x, y, w, h)
ctypes.ArgumentError: argument 3: <type 'exceptions.TypeError'>: wrong type


I would be grateful if someone could provide me with some clues as to how I can get FretsOnFire working.

Thanks in anticipation

Chris
:guitar:

---

### Post by Chris Riley on 2007-12-15
Ooops! Title should read "FretsOnFire".

---

### Post by swedishlf on 2007-12-15
I had the same problem on the same setup.  To get it working I removed it via apt-get:
```
sudo apt-get remove fretsonfire --purge
```

then I downloaded it from [the FretsOnFire sourceforge page.]("http://fretsonfire.sourceforge.net/")

Extracted to $HOME/apps

then just run: ```
$HOME/apps/FretsOnFire/FretsOnFire
```

It's very slow the first time I load up a song, but other than that it seams to be working great!

---

### Post by Chris Riley on 2007-12-16
Thanks Swedishlf, I now have the graphics, and have tried to play the game after first running through the tutorial.

Am I supposed to get the sound of the notes I play whilst running the game? I can Hear Jurgen Whats-his-flip talking during the tutorial, but thats all. Do I hear nothing because I'm missing the notes?

Or am I a numpty?

Chris
:lolflag:

---

### Post by swedishlf on 2007-12-16
I haven't played too much, but that's how it works for me.  I only get music when I've hit notes, I just assumed that's how it was supposed to be.

Now I just need a keyboard that's more comfortable to rock out on :guitar:

---

