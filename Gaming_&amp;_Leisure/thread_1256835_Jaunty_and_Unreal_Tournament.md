---
title: "Jaunty and Unreal Tournament"
date: 2009-09-03
forum: Gaming &amp; Leisure
---

### Post by shoaibi on 2009-09-03
On torrent i found a file where a guy made a custom installation of UT for linux, all you needed was run setup.sh. I download and tried to install, it installed on 32 bit just fine, but kept bitching on 64bit that its not supported. I ran:
```

linux32 sh setup.sh

```

and this time it installs fine, but when i try to play, i get:
```

[364][shoaibi@blade:/media/ut]$ ut                                                                                                                 (03/09/09 14:16:58)
Unreal engine initialized
Bound to SDLDrv.so
Joystick [0] : Unknown Joystick
SDLClient initialized.
Bound to Render.so
Lighting subsystem initialized
Rendering initialized
LoadMap: Entry
Bound to Fire.so
Case-insensitive search: Botpack -> ..\System\BotPack.u
Bound to IpDrv.so
appError called:
Class Actor Member Owner problem: Script=48 C++=52
Executing UObject::StaticShutdownAfterError
Executing USDLClient::ShutdownAfterError
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down

```

Any ideas?

---

