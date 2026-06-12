---
title: "Help with Mupen64plus key config"
date: 2013-01-30
forum: Gaming &amp; Leisure
---

### Post by Xslymaster on 2013-01-30
Ok I have downloaded Mupen64Plus and somehow got it to run... But i do not know how to change the controls. It runs way better in my opinion then Project 64 but i can't control anything. The controls are in code and i'm a noob at that. Here is what it looks like:

; InputAutoCfg.ini for Mupen64Plus SDL Input plugin

[Keyboard]
plugged = True
plugin = 2
mouse = False
DPad R = key(100)
DPad L = key(97)
DPad D = key(115)
DPad U = key(119)
Start = key(13) 
Z Trig = key(122)
B Button = key(306)
A Button = key(304)
C Button R = key(108)
C Button L = key(106)
C Button D = key(107)
C Button U = key(105)
R Trig = key(99)
L Trig = key(120)
Mempak switch = key(44)
Rumblepak switch = key(46)
X Axis = key(276,275)
Y Axis = key(273,274)
_____________________________________
I do not know what number is what key at all. If you could help me with it that would be spectacular!
<3 Xslymaster

---

### Post by deadflowr on 2013-01-30
When you enter your command for mupen64plus add --saveoption 
Example:

```
mupen64plus --saveoptions /home/blah/gamefile
```

The saveoption command will add the configuration to the mupen config file in the home folder, located in the hidden folder /home/yourname/.config/mupen64plus/mupen64plus.cfg.
(ctrl + h to show hidden folders and file)

Use the keys in this link to figure out which key is which:

[http://svn.libsdl.org/tags/SDL/release-1.2.7/include/SDL_keysym.h]("http://svn.libsdl.org/tags/SDL/release-1.2.7/include/SDL_keysym.h")


This config file is easier to work with since it doesn't need to be edited in root, and you can tweak it endlessly without sudoing over and over.

When it's all set just run mupen64plus /filename.

Run mupen64plus --help to see a list of extra options like resolution and what nots.

---

