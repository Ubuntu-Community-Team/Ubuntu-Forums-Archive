---
title: "compiz (core) - Error: Couldn't load plugin 'emerald'"
date: 2007-06-30
forum: Desktop Effects &amp; Customization
---

### Post by medeshago on 2007-06-30
That's what i get when I type  compiz --replace -c emerald & in the command line.
Everything works fine with beryl, but with compiz i don't have window decoration. I uninstalled Beryl before installing compiz and didn't work either.

My xorg.conf:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic E70f+-4"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option "AddARGBVisuals" "True"
    Option         "AllowGLXWithComposite" "True
    Option         "metamodes" "CRT: 1280x1024 +0+0; CRT: 832x624 +0+0; CRT: 800x600 +0+0; CRT: 720x400 +0+0; CRT: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection
```


Thanks.

---

### Post by hyperair on 2007-06-30
Make sure you have the decoration plugin enabled in CompizConfig Settings Manager

---

### Post by medeshago on 2007-06-30
It's enabled.

---

### Post by hyperair on 2007-07-01
Check the outputs of 
```

apt-cache policy emerald

```

and 

```

apt-cache policy compiz

```

---

### Post by medeshago on 2007-07-02
Post compiz

```
medeshago@nosotros:~$ apt-cache policy emerald
emerald:
  Instalados: 0.3.0+git20070621~3v1ubuntu0
  Candidato: 0.3.0+git20070621~3v1ubuntu0
  Tabla de versión:
 *** 0.3.0+git20070621~3v1ubuntu0 0
        500 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages
        100 /var/lib/dpkg/status
     0.2.1-0ubuntu1 0
        500 [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) feisty/universe Packages
```

```
medeshago@nosotros:~$ apt-cache policy compiz
compiz:
  Instalados: 1:0.5.1+git20070629~3v1ubuntu2
  Candidato: 1:0.5.1+git20070629~3v1ubuntu2
  Tabla de versión:
 *** 1:0.5.1+git20070629~3v1ubuntu2 0
        500 http://download.tuxfamily.org feisty/eyecandy Packages
        100 /var/lib/dpkg/status
     1:0.5.0-0ubuntu1 0
        500 http://ubuntu.moshen.de feisty/eyecandy Packages
     1:0.3.6-1ubuntu13 0
        500 http://cl.archive.ubuntu.com feisty/main Packages
     1:0.3.6-0ubuntu5 0
        500 http://gandalfn.club.fr feisty/motu Packages
```

I keep geting:

medeshago@nosotros:~$ compiz --replace emerald
compiz (core) - Error: Couldn't load plugin 'emerald'

---

### Post by hyperair on 2007-07-02
That's because you have the wrong command!
It's ```
compiz --replace -c emerald
``` not ```
compiz --replace emerald
```

If that doesn't work, try running compiz --replace and emerald --replace one after another. compiz first.

---

### Post by medeshago on 2007-07-02
```
medeshago@nosotros:~$ compiz --replace -c emerald
compiz (core) - Warn: Unknown option '-c'

compiz (core) - Error: Couldn't load plugin 'emerald'
```

```
medeshago@nosotros:~$ compiz --replace
#I get nothing back but no window decoration
```
```

medeshago@nosotros:~$ emerald --replace

(emerald:7751): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7751): Wnck-WARNING **: Unhandled action type (nil)

# i get that message repeteadly and still no window decoration

```

---

### Post by hyperair on 2007-07-02
Well, is your compiz even working to begin with? Do you have any compiz features? Wobbly windows? Cube?
Emerald's error messages always pop up, but they probaably don't mean anything. For me, Emerald just runs even with those error messages.

---

### Post by medeshago on 2007-07-02
I have opacity control, but nothing else.

---

### Post by hyperair on 2007-07-03
Did you by any chance disable every other plugin in the CompizConfig Settings Manager?

---

### Post by medeshago on 2007-07-03
Almost everything is enabled.

---

### Post by hyperair on 2007-07-03
Make sure your packages are fully up to date.
```

sudo apt-get update
sudo apt-get upgrade

```

Because I only had that kind of output sometime back, and there are updates almost every day.

---

### Post by Bachstelze on 2007-07-03
When you do

```
compiz --replace &
```

You'll have no window decoration but to see if Compiz is working correctly, you can try to move a window by holding the Alt key and dragging it. If it works, try to load another window decorator, for example

```
gtk-window-decorator --replace &
```

---

### Post by medeshago on 2007-07-03
Everything is upgraded. I can't move the windows nor anything related. I do have opacity control.

medeshago@nosotros:~$ gtk-window-decorator --replace &
[2] 11736
medeshago@nosotros:~$ 
(gtk-window-decorator:11736): Wnck-WARNING **: Unhandled action type (nil)
#no window decoration apperas.

---

### Post by hyperair on 2007-07-03
I think you've got another composite manager running. Could you try these commands:
```

pidof kompmgr
pidof xcompmgr

```

Those two conflict with Compiz.

---

### Post by medeshago on 2007-07-03
Nothing happened, still no window decoration

---

