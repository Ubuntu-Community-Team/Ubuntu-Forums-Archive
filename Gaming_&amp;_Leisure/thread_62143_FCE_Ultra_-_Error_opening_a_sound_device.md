---
title: "FCE Ultra - Error opening a sound device"
date: 2005-09-03
forum: Gaming &amp; Leisure
---

### Post by rah on 2005-09-03
Does anyone know what I can do to fix this?  Otherwise this NES emulator seems to be running fine, but it's mute.  In the shell it says:

Initializing sound...Error opening a sound device.

My audio CDs play fine, so I'm not sure what the problem is.

---

### Post by rah on 2005-09-03
I fixed this by doing the following:

killall esd

before loading the rom.

---

### Post by rafakl on 2005-09-04
ESD is a bad sound server with games.

with every game you play in linux, its very probable that you will not have sound.

there is a guide to fix it permanently (i dont remember the link), without having to type "killall esd" every time you play a game.

---

### Post by rah on 2005-09-04
Thanks for the advice.  I saw that link you're talking about, but I didn't bother with it, because so far the NES games in fceu are the only games I've gotten to work.  If it's like this with MAME and other emulators, then I may have to do as you say.

---

### Post by The Unmaker on 2008-07-09
> **rah said:**
> Thanks for the advice.  I saw that link you're talking about, but I didn't bother with it, because so far the NES games in fceu are the only games I've gotten to work.  If it's like this with MAME and other emulators, then I may have to do as you say.

Inputting killall esd doesn't help me. I still get the same error. I do have the alsa-oss drivers installed, so I'm not sure.

---

### Post by The Unmaker on 2008-07-14
> **The Unmaker said:**
> Inputting killall esd doesn't help me. I still get the same error. I do have the alsa-oss drivers installed, so I'm not sure.

Seems that using killall esd doesn't do it, but I finally got the sound to work with no other input from me. It just started working when I made sure ALL possible programs tying up a sound server (this includes firefox, aMSN, any chat clients, and music/movie players) were closed and no residual programs were still using the sound server. No one posted back, so I guess this seems like an obvious solution (it isn't). 

Can anything be done to mitigate the multiplexing issues (if that's what I can refer them as) in Linux? An example would be that using a flash application ties up some sound server (don't know which) and then sound won't work in FCEU or aMSN and vice versa.

---

### Post by peacimowen on 2010-05-13
I installed a number of things, but what finally fixed this error for me was listed here:

[http://www.esdebian.org/foro/21805/fceu-error-initializing-sounderror-opening-sound-device-solucionado](http://www.esdebian.org/foro/21805/fceu-error-initializing-sounderror-opening-sound-device-solucionado)

Which simply says to install oss-alsa and oss-compat and then modprobe snd_pcm_oss (after checking that it's available with lsmod)

---

