---
title: "[help] xorg.conf"
date: 2006-06-05
forum: Desktop Environments
---

### Post by Krpano on 2006-06-05
Guys,
Ive been reading about and waiting for help in other forums about this problem.

Everything works here, i just want my second display(TV-out) to show a lower resolution (800x600).
Actually is displaying a clone from my primary monitor, which is what i want but the TVout is emulating the resolution from the primary.

Here is my xorg.conf

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "aticonfig-Screen[0]" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

    # path to defoma fonts
    FontPath     "/usr/share/X11/fonts/misc"
    FontPath     "/usr/share/X11/fonts/cyrillic"
    FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath     "/usr/share/X11/fonts/Type1"
    FontPath     "/usr/share/X11/fonts/100dpi"
    FontPath     "/usr/share/X11/fonts/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load  "i2c"
    Load  "bitmap"
    Load  "ddc"
    Load  "dri"
    Load  "extmod"
    Load  "freetype"
    Load  "glx"
    Load  "int10"
    Load  "type1"
    Load  "vbe"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "ch"
    Option        "XkbVariant" "fr"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
    Option        "Device" "/dev/input/mice"
    Option        "Protocol" "ExplorerPS/2"
    Option        "ZAxisMapping" "4 5"
    Option        "ButtonMapping" "1 2 3 6 7"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]"
    HorizSync    30.0 - 70.0
    VertRefresh  50.0 - 160.0
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]"
    Driver      "fglrx"
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]"
    Device     "aticonfig-Device[0]"
    Monitor    "aticonfig-Monitor[0]"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1280x1024" "1152x864" "1024x768" "800x600"
    EndSubSection
EndSection

Section "DRI"
    Mode         0666
EndSection
```

I have Dapper + XGL.
I just want my TVout to be 800x600.

---

### Post by zerwas on 2006-06-05
[LIST]
[*]You should really consult the documentation of your ati driver in /usr/share/doc before posting a thread :).

[*] See
```
aticonfig --help
```
and options --resolution and --resolution2 for help.


[*] Also, i found interesting [Google results]("http://www.google.de/linux?hl=de&q=resolution+tvout+OR+tv-out+OR+%22tv+out%22&btnG=Suche&meta=")

[/LIST]
Greetings,
zeRwas

---

