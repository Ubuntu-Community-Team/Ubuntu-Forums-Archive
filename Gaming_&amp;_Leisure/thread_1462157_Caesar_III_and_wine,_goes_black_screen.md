---
title: "Caesar III and wine, goes black screen"
date: 2010-04-25
forum: Gaming &amp; Leisure
---

### Post by darthdalais on 2010-04-25
Hi, Im using ubuntu since hardy, and this is the first time I have to post a problem. I bought Caesar III yesterday, and installed fine on wine.

The problem is when I launch the game, I can hear the sounds and the music, but the graphics dont load, and all I get is a black screen.

Im using karmic and have installed wine 1.1.43, winetricks I deactivated compiz, tried -opengl and without it, and the problem persisted.

This is what a i get on the log

```
~/.wine/drive_c/SIERRA/Caesar3$ wine c3.exe
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f624,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
```

It happened the same with Half-Life, and I think it could be a problem of wine/ubuntu config, because on the WineHQ site it seems to work these games perfect.

Anyone could guide me please?:(

---

