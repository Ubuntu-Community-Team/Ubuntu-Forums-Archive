---
title: "Which one; Beryl, compiz, or Compiz confusion???"
date: 2007-10-02
forum: Desktop Effects &amp; Customization
---

### Post by Dwiman89 on 2007-10-02
What is the difference between compiz fusion,beryl,and compiz. I have duel monitors. I have which one shoud l install that is the coolest. i tryed to enable desktop effects but it didn't work.The windows didnt have a title bar.I had Beryl working fine on this box without duel monitors. I have upgraded the graphics card sence then and reinstalled ubuntu. I would REALLY like to know....
I have a AMD Athlon 2200+ 1.8GHz, 512MB RAM, with a NVIDIA GeForce FX 5200.

---

### Post by armware on 2007-10-02
compiz was the beginning, when it forked beryl was born. work on compiz was for stability, while work on beryl was features.
compiz fusion is the result of recombining the two.

these answers are readily available, try the search feature.

no title bar means no window management software is running. in gnome, it's metacity, in kde it's kwin. beryl can use either, as well as many others, such as emerald.

try launching your window manager next time you don't have title bars. again, these answers can be found via the search feature.

---

### Post by Jussi Kukkonen on 2007-10-02
> **armware said:**
> no title bar means no window management software is running. in gnome, it's metacity, in kde it's kwin. **beryl can use either, as well as many others, such as emerald**.

This is actually false. Beryl **is** a window manager, it does not use metacity or kwin. Beryl does have different window decoration modes that look like Metacity and Kwin.

---

### Post by Dwiman89 on 2007-10-02
ok cool. I guess Compiz Fusion would be the best. The whole Beryl will mess your system up kinda scares me. can you direct me to a good Howto for installing Compiz fusion?

---

### Post by Dwiman89 on 2007-10-02
wich one does Desktop effects use?

---

### Post by bimmerd00d on 2007-10-02
> **Dwiman89 said:**
> ok cool. I guess Compiz Fusion would be the best. The whole Beryl will mess your system up kinda scares me. can you direct me to a good Howto for installing Compiz fusion?

Gotta learn to use the search feature here if you want some decent help.  Check the main Desktop Effects and Customization forum, there are some stickied threads with the instructions you're looking for.  Compiz-Fusion is the best of both worlds, it's the one you want.

---

### Post by Dwiman89 on 2007-10-02
Thanks for the feed back. Ill see what i can find. i just get a little irritated at the very general results from searching.

---

### Post by Dwiman89 on 2007-10-03
I followd a gide and got Compiz fusion from synaptic. but when i start it, there are no window borders. can anyone please help?

---

### Post by kellemes on 2007-10-03
sudo aptitude install emerald emerald-themes

compiz --replace emerald

---

### Post by anarchist_hippy on 2007-10-03
Are there any red diamond in your taskbar? I mean beryl Manager... If there's one, right click on it and select a window manager... 

If there's nothing like this, firstly remove all beryl things, then restart (or logout/login). After restart, normal window borders should seen... And open adept and install beryl (and it's depencies..), and especially install "beryl manager". Restart again... And If still there's no border, you can re-built them with beryl manager... 

And one other thing, I suggest (think) that, Beryl can crash randomly with your configuration ;)

---

### Post by screaminj3sus on 2007-10-03
Compiuz Fusion, better than compiz or beryl, incorporates the ebst of both, stable and feature rich it is goign to be included by default in gitsy, fiesty currently uses compiz.

---

### Post by Dwiman89 on 2007-10-03
> **anarchist_hippy said:**
> Are there any red diamond in your taskbar? I mean beryl Manager... If there's one, right click on it and select a window manager... 

If there's nothing like this, firstly remove all beryl things, then restart (or logout/login). After restart, normal window borders should seen... And open adept and install beryl (and it's depencies..), and especially install "beryl manager". Restart again... And If still there's no border, you can re-built them with beryl manager... 

And one other thing, I suggest (think) that, Beryl can crash randomly with your configuration ;)
Nope ther is no red diamond. I installd compiz fusion. should i not need anything beryl...right. I also have duel monitors with twinview if that would have anything to do with it?

---

### Post by taehC on 2007-10-04
so far compiz-fusion is really kind of slow and unstable at the time and i think it is still a pre-release?  but beryl ran great and had lots of features i would run beryl or compiz fusion.  if u got gutsy gibbon go for compiz fusion.  if u got feisty fawn go for beryl.

---

### Post by bmdavis on 2007-10-04
To get the bars back, try this--

Under Compiz-Config, "window decoration", fill in the Command as 

'gtk-window-manager'

Let me know if it works.

---

### Post by Dwiman89 on 2007-10-04
> **bmdavis said:**
> To get the bars back, try this--

Under Compiz-Config, "window decoration", fill in the Command as 

'gtk-window-manager'

Let me know if it works.
Nope this didn't work, the window borders went awy when i typed;
```
compiz --replace
```

There is also no cube to rotate even after it is checked in the settings. Do you also think it would be a good idea to try Beryl. If so can you give me a good URL to a howto for beryl. Also do i need to remove compiz confusion if i do need to swich to Beryl.

---

### Post by armware on 2007-10-04
when i loose my window decorations, i run just  compiz  (without --replace). seems to figure it out, granted sometimes nothing on the title bar is drawn, but minimize/restore or even just switch windows and they'll get drawn.

---

### Post by Dwiman89 on 2007-10-04
I dont know if this helps;
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:56:12 PST 2006

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
    ModelName      "Compaq"
    HorizSync       31.0 - 48.0
    VertRefresh     60.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1024x768 +1024+0, CRT-1: nvidia-auto-select +0+0; CRT-0: 800x600 +0+0, CRT-1: nvidia-auto-select +800+0; CRT-0: 640x480 +0+0, CRT-1: nvidia-auto-select +640+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

I have red several threds and they suggest AIGLX. I though this is for edjy but i have fiesty. If this it the case how do i fix it?

---

### Post by Dwiman89 on 2007-10-04
tis is what i get from running the command in terminal;
```
 compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2048x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)

(emerald:11620): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 
```

I hope this helps you help me...

---

### Post by Rupertronco on 2007-10-05
> **anarchist_hippy said:**
> Are there any red diamond in your taskbar? I mean beryl Manager... If there's one, right click on it and select a window manager... 

If there's nothing like this, firstly remove all beryl things, then restart (or logout/login). After restart, normal window borders should seen... And open adept and install beryl (and it's depencies..), and especially install "beryl manager". Restart again... And If still there's no border, you can re-built them with beryl manager... 

And one other thing, I suggest (think) that, Beryl can crash randomly with your configuration ;)

He's using compiz fusion, not beryl. 

You don't need AiGLX if you have the newest nvidia drivers. Nvidia has it's own TMP (texture from pixmap) support. 

Remove the gtk-window-decorator option. 

Then go to the screen section of your xorg.conf and put this in:
```
Option         "AddARGBGLXVisuals" "True"
```

After that type ```
compiz --replace
```
And ```
 emerald --replace
```

---

### Post by Dwiman89 on 2007-10-05
Hi, I actually tryed something else before i checked this. I got my borders back by going to the compiz settings and enabling window decoration and putting the line ''gtk-window-decorator'' under command.
There is still issuse though. there are effects not working such as the cube doesnt work. I do have two monitors enabled with Twinview. 
This is what i get when i enable compiz in terminal;
```
derrick@Hambone:~$ compiz --replace
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format



```
Pleas help?

---

### Post by Rupertronco on 2007-10-05
What else did you change if you weren't seeing that before?

---

### Post by Dwiman89 on 2007-10-05
All seems to be working now. I dont really know how  but it is.

---

