---
title: "Can't make games go fullscreen"
date: 2008-12-20
forum: Gaming &amp; Leisure
---

### Post by Envergure on 2008-12-20
When I set fullscreen games (Urban Terror, Nexuiz, etc.) to the full resolution of my screen they insist on being windowed, and won't respond to mouse input.  To get them fullscreen and mouse-responsive I have to set them to a smaller resolution (which is difficult to do with only the keyboard in some games).

Another, possible related problem is as follows:  The screensaver goes off after a few minutes in fullscreen games.  Whatever governs when it's triggered thinks the computer is idle when fullscreen games are active.

---

### Post by theevilhamster on 2008-12-20
Are u certain that you have the right resolution for your screen? Try this;

```
xrandr
```.

---

### Post by StevenHarper on 2008-12-20
Have you tried setting the visual effects to normal

System 
Preferences
Appearance


Visual Effect (Tab)
choose : none

---

### Post by theevilhamster on 2008-12-20
> **StevenHarper said:**
> Have you tried setting the visual effects to normal

System 
Preferences
Appearance


Visual Effect (Tab)
choose : none

Good idea! compiz may be causing problems too try this;
```
metacity --replace&
```.

This will disable compiz. to re-enable use this.

```
compiz --replace&
```.

---

### Post by crazyfuturamanoob on 2008-12-21
For the screensaver problem, disable screensaver temporarily before playing the game.

System->Preferences->Screensavers & uncheck the box

---

