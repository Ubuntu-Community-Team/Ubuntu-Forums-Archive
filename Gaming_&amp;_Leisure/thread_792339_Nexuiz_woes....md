---
title: "Nexuiz woes..."
date: 2008-05-12
forum: Gaming &amp; Leisure
---

### Post by lackofcreativity on 2008-05-12
Just downloaded Nexuiz 2.4.2, love the new features. A couple bugs from 2.4 weren't cleaned up for me. I'll try to be orderly about it...

1. No SMP support. Any workaround you guys use?

2. No sound in GLX. I haven't bothered with SDL because of 3. I have to run:
```
./nexuiz-linux-x86_64-glx -sndspeed 48000 -sndstereo
``` I don't really put up a fuss about it because I have a workaround, but it *is* getting annoying...

3. SDL won't stay in fullscreen. It immediately flickers and goes back to windowed, where it is not controllable. I click on it rapidly and it goes back to fullscreen for a second, then back to windowed. Again, there is a workaround (using GLX) but if that stops working, I'm up a creek...

4. The most annoying. At a random time, the sound stops, some of the lighting effects turn off, and the FPS rate drops down to 20. Since my normal FPS is in the 55-90 range, it runs at a perfect 20 constantly. Obviously this makes it barely playable and the only thing I can do is quit and start it back up. This is obviously annoying when playing CTF online.

I would greatly appreciate any help! Thanks guys!

---

### Post by p388l3s on 2008-05-12
In my previous ubuntu install, Gutsy I noticed the screen saver was kicking in and would slow my frame rate down until I moved the mouse on the desktop, this may be your problem for #4

As for your other problems you'll need to post your machine specs and which gpu driver your using before anyone can be really helpful

---

### Post by Perfect Storm on 2008-05-13
> 3. SDL won't stay in fullscreen. It immediately flickers and goes back to windowed, where it is not controllable. I click on it rapidly and it goes back to fullscreen for a second, then back to windowed. Again, there is a workaround (using GLX) but if that stops working, I'm up a creek...

Sound likely to disable compiz when playing in full screen. Some games does that if compiz is enable. Just simple disable compiz when playing or make a script for it.

---

### Post by lackofcreativity on 2008-05-13
Thanks...system specs:
AMD Athlonx2 4200+ 2.2 GHz
x86-64 Ubuntu 8.04
Radeon X1300 PRO 256 MB using the fglrx driver

Gonna try disabling the screensaver and Compiz, thanks for the help!

---

### Post by lackofcreativity on 2008-05-13
Yeah, GLX works now! Maybe I'll try SDL, just got back from drumline practice. (go tenors :) )

---

