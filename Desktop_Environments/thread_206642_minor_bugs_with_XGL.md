---
title: "minor bugs with XGL"
date: 2006-06-30
forum: Desktop Environments
---

### Post by grigory_k on 2006-06-30
So, here it goes.
I recently installed an ultimate eye-candy named XGL, following one of the up-to-date instructions on compiz forums, and everything seemed to be fine at first...
But then, as I was playing around with those jello windows, ubuntu just logged out, showing me gdm screen. It logges in without a problem, but the same thing(log out) happens again after some time.
I looked at the error messages, then tried to run xgl in 'nested' mod(in a little window), just to see error messages in terminal, and here is what it tells me:
>  *********************************WARN_ONCE*********************************
File radeon_mm.c function radeon_mm_alloc line 216
Ran out of GART memory!
Please consider adjusting GARTSize option.
***************************************************************************
  id: 117f000101000115168285400000074960000
  handle: 1
  connection: (nil)
  properties:
    ((name "RestartCommand") (type "LISTofARRAY8") (value "gnome-wm") (value "--sm-client-id") (value "default0"))
    ((name "Program") (type "ARRAY8") (value "metacity"))
    ((name "UserID") (type "ARRAY8") (value "grigory"))
    ((name "RestartStyleHint") (type "CARD8") (value " "))
    ((name "ProcessID") (type "ARRAY8") (value "7513"))
    ((name "CurrentDirectory") (type "ARRAY8") (value "/home/grigory"))
    ((name "_GSM_Priority") (type "CARD8") (value " "))
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Error: Could not get dma buffer... exiting
The application 'gnome-settings-daemon' lost its connection to the display :10.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'gnome-panel' lost its connection to the display :10.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'nautilus' lost its connection to the display :10.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'totem' lost its connection to the display :10.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'update-notifier' lost its connection to the display :10.0;
most likely the X server was shut down or you killed/destroyed
the application.
gnome-window-decorator: Fatal IO error 104 (Connection reset by peer) on X server :10.0.
X connection to :10.0 broken (explicit kill or server shutdown).
xinit:  connection to X server lost.

I have Radeon 9600 Atlantis video card(not ATI but Sapphire, 256 mb).

Any help would be greatly appreciated.

---

### Post by Jango on 2006-06-30
Well.... I guess u don't have enough GART memory available.

Try this:

1) open xorg.conf
2) put 

```
Option "GARTSize" "64"
```

under "Device" section

good luck!

---

### Post by grigory_k on 2006-06-30
2Jango:
Tried that, seems to be working fine for now.
Tried killing it with 4 videos in fullscreen mode and spinning the cube - but it's holding fine :)
Yay, I can finally enjoy XGL's goodness :) Thanks!

---

### Post by Jango on 2006-06-30
[QUOTE=grigory_k]2Jango:
Tried that, seems to be working fine for now.
Tried killing it with 4 videos in fullscreen mode and spinning the cube - but it's holding fine :)
Yay, I can finally enjoy XGL's goodness :) Thanks![/QUOTE]

my pleasure :grin:

---

