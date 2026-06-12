---
title: "Relative screen positioning"
date: 2008-02-01
forum: Desktop Environments
---

### Post by robaldred on 2008-02-01
Hi am running two monitors at different resolutions, I want to align them at the bottom rather than at the top, because its bugging me that menus disappear into the dead zone at the bottom of my lower resolution screen. My main screen is running 1920 x 1200 the other is 1280 x 1024

This is the layout section with it working correctly but aligned at the top
```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0        "Default Screen"
        Screen 1        "SHARP Screen" LeftOf "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        Option "Xinerama" "on"
EndSection

```

I have tried to use relative positioning to align it at the bottom, but X complains about the screen line when i start it with the following...

```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0        "Default Screen"
        Screen 1      "SHARP Screen" Relative "Default Screen" -1280 176
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        Option "Xinerama" "on"
EndSection

```

Anyone know what I am doing wrong?
Many thanks

Rob

---

### Post by robaldred on 2008-02-04
bump

---

