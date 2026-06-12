---
title: "Installing Unreal Tournament GOTY"
date: 2009-03-17
forum: Gaming &amp; Leisure
---

### Post by nathand28 on 2009-03-17
I've tried to follow [these]("http://ubuntuforums.org/showthread.php?t=289796") instructions on how to install it ( by GOTY I mean the first game ) on Intrepid. So far, when I try to run it with a launcher pointing to /usr/games/ut/playut for the command, nothing happens. I tried these in the terminal:
```
cd /usr/games/ut/playut
./ut
```
But come up with this:
```
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

Seems like there's a lot of missing entries..

[Here's]("http://mandrivausers.org/index.php?showtopic=2283") the link for  some more information.

I think it works if you paste this into a terminal:
```
#!/bin/sh

for i in /usr/games/ut/Maps/*.unr.uz
do ucc decompress $i
done
```

---

