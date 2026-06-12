---
title: "Help with Unreal Tournament"
date: 2007-06-12
forum: Gaming &amp; Leisure
---

### Post by robert-s on 2007-06-12
I installed Unreal Tournament (G.O.T.Y edition) and things seemed to go well, but when I start it up just seems to crash. Here's what the console says:
```
robert@ubuntu:~$ /usr/local/games/ut/ut
Unreal engine initialized
Bound to SDLDrv.so
Joystick [0] : Unknown Joystick
SDLClient initialized.
Bound to Render.so
Lighting subsystem initialized
Rendering initialized
LoadMap: Entry
Failed to load 'Entry': Can't find file 'Entry'
Failed to load 'Level None.MyLevel': Can't find file 'Entry'
appError called:
Failed to enter Entry: Can't find file 'Entry'
Executing UObject::StaticShutdownAfterError
Executing USDLClient::ShutdownAfterError
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down
```
Anyone know what that means?

---

### Post by WeeJeWel on 2007-06-12
> Failed to load 'Level None.MyLevel': Can't find file 'Entry'
This sounds weird. Have you tried to run it as root yet?

---

### Post by robert-s on 2007-06-12
> **WeeJeWel said:**
> This sounds weird. Have you tried to run it as root yet?
Yes, the same thing happens when I run as root.

Also I forgot to say what I'm running on:

Feisty
Athlon XP 2500
1GB RAM
Geforce 6600GT (+ the nvidia drivers)

---

### Post by mtalexan on 2007-06-13
Looks like you might not have the file(s) for your map(s) in the right place.  It tried to load map "Entry" by couldn't find it so it tried to load it's fallback and couldn't find that either.  Check your map location and make sure all your paths are mapped correctly.

---

### Post by robert-s on 2007-06-14
> **mtalexan said:**
> Looks like you might not have the file(s) for your map(s) in the right place.  It tried to load map "Entry" by couldn't find it so it tried to load it's fallback and couldn't find that either.  Check your map location and make sure all your paths are mapped correctly.

Thanks for the response. How would I do that? My map files seem to be in /usr/local/games/ut/Maps.

---

