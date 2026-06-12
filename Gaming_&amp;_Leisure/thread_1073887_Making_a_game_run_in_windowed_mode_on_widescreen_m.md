---
title: "Making a game run in windowed mode on widescreen monitor"
date: 2009-02-18
forum: Gaming &amp; Leisure
---

### Post by stchman on 2009-02-18
Hello all, I have a question.

I have some older games that WINE runs just fine.  Only problem is that since I upgraded my LAN machine to a widescreen monitor some of my games do not support the widescreen resolutions.

Is there a way to make an app like an openGL game run in a windowed mode.  I would prefer to do it via the command line so it can be implemented in a script.  This would take care of the game having that stretched out look on a widescreen monitor.

The games are Half Life, Kingpin, SoF.  I know they are old, but they are fun to play at a LAN party.  As you can see these are Quake II based games and the Quake II engine does not support widescreen resolutions.

I also play UT and UT does support widescreen by editing the unrealtournament.ini file.

Thanks.

---

### Post by Vadi on 2009-02-18
I think you just go into game options and disable fullscreen.

---

### Post by Rytron on 2010-06-13
How could I force astromenace to run in a window of 800x600?

---

### Post by hikaricore on 2010-06-13
> **Rytron said:**
> How could I force astromenace to run in a window of 800x600?

Aside from going into the video config and setting the resolution to 800x600 and disabling fullscreen?..

---

### Post by DoktorSeven on 2010-06-13
You can force any Wine program into a window by running **winecfg** and choosing the Emulate a Virtual Desktop option in the Graphics tab (and setting a suitable window resolution underneath).

Any native games, though, you'll have to manually set them to use a window either by their options file or in-game options.

---

### Post by Rytron on 2010-06-14
> **DoktorSeven said:**
> You can force any Wine program into a window by running **winecfg** and choosing the Emulate a Virtual Desktop option in the Graphics tab (and setting a suitable window resolution underneath).

Any native games, though, you'll have to manually set them to use a window either by their options file or in-game options.

I see. Thank you DoktorSeven.

---

