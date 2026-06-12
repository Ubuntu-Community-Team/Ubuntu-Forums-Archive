---
title: "Pysol Sound Problem"
date: 2005-12-14
forum: Desktop Environments
---

### Post by tofuconfetti on 2005-12-14
I have a strange sound issue with Pysol.  If I run it from a terminal prompt as a user or as root, I have full sound.  If I run it from the gnome menu (I added it manually), I get no sound and get a message on startup that it can't find the sound server.  The exact message is

   "the pysolsoundserver modules was not found" 
   "sounds and background music will be disabled"

Once at the terminal, I got this ...
> 
Traceback (most recent call last):
  File "/usr/share/games/pysol/pysolaudio.py", line 229, in startServer
    self.audiodev.init()
error: unable to open audio: No available audio device
PySol: could not connect to pysolsoundserver, sound disabled.

I put myself in the audio group and games group with no luck.

Does anyone have any ideas?

---

