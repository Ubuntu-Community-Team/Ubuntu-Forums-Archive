---
title: "GFCEU running too fast"
date: 2007-11-04
forum: Gaming &amp; Leisure
---

### Post by BigSilly on 2007-11-04
Hiya Linux fans. I'm currently using the NES emulator FCEU with the GFCEU GUI to control it. I'm noticing that it's running games at what seems to be almost double the normal speed. I can't see anything in the menu's to control such a thing, so does anyone here have an idea of what I need to do to control the speed? Is there perhaps a better GUI frontend for this program than GFCEU?

Cheers in advance. :)

---

### Post by alyndaker on 2008-02-25
I am having a very similar problem.  

The speed issue is not caused by GFCE, but rather by the emulator itself, FCEU.  I've tried running it from the command line with various options and so far none have caused the speed to change.  It also does not appear that there is an option for speed throttling.  Does anyone have any suggestions?

---

### Post by BigSilly on 2008-02-25
I tend to prefer FakeNES anyway nowadays, since I still have the speed problem on GFCEU. But you're right I expect - it's the FCEU emu core where the problem lies. 

If anyone has a fix for this I would be very pleased to hear it too. Thanks in advance.

---

### Post by acoustibop on 2008-02-25
pSX Emulator used to have a problem like this - it seemed to be caused by having a monitor with a refresh rate running at twice the fps of the game (i.e. a monitor running at 100Hz for a PAL game (50fps), or 120Hz for an NTSC-US game (60fps).

AIR this was a Windows problem and linked to VSync, which makes it unlikely to be the cause here, but if you do have a monitor using a refresh rate that's twice the fps of the game, it might be worth trying a different refresh rate just to make sure. ;)

---

### Post by GSZX1337 on 2008-02-25
I remember having a problem like this. IIRC, I disabled OpenGL and everything was peachy. (Mmm, peaches.)

---

### Post by punkrockguy318 on 2008-07-02
You can use the + and - keys to control emu speed.

If you want, you can try the fceu in the latest subversion and let a fceu dev (me) if you still have the problem

---

