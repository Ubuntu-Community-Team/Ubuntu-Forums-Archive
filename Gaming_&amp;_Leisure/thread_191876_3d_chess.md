---
title: "3d chess?"
date: 2006-06-08
forum: Gaming &amp; Leisure
---

### Post by delfick on 2006-06-08
hi all

Is there a free 3d chess game for linux....

or are the only free linux chess games 2d?

thnx

---

### Post by seth0x2b on 2006-06-08
Try [http://glchess.sourceforge.net/](http://glchess.sourceforge.net/)

Cheers

---

### Post by Gustav on 2006-06-08
There is also 3Dchess which is in the repos. (It hasn't been upgraded since warty though so it may not be very pretty)

---

### Post by delfick on 2006-06-08
cool, i looked at glchess, and that is the kind of thing i'm looking for, thnx

the problem is, after i installed it, when i went to open it, the terminal tells me this
> Traceback (most recent call last):
  File "/usr/share/games/glchess/glchess.py", line 13, in ?
    import ui
  File "/usr/share/games/glchess/ui/__init__.py", line 2, in ?
    import gtkui
  File "/usr/share/games/glchess/ui/gtkui/__init__.py", line 3, in ?
    import gtkui
  File "/usr/share/games/glchess/ui/gtkui/gtkui.py", line 23, in ?
    from OpenGL.GL import *
ImportError: No module named OpenGL.GL


I'm not sure if you people'd be able to help me, but if you can that would be great...
thnx

---

### Post by Gustav on 2006-06-08
You could try to install python-opengl (sudo apt-get install python-opengl) and see if it helps.

---

### Post by delfick on 2006-06-08
awsome, now it works, thnx very much for your help...:D:D:D:D

---

### Post by charlieg on 2006-06-08
There's also [pouetChess]("http://pouetchess.sourceforge.net/") which seems to be progressing nicely.

---

### Post by delfick on 2006-06-09
that looks fantastic!

the only problem is that i'm fairly new to linux and have no idea where to get this SDL and SDL-image it says it needs...

you don't have to help me but if u do....thnx

:D

---

### Post by Niamor on 2006-06-09
well I just had to type that in a terminal : sudo apt-get install libsdl-image1.2
And it worked fine :wink:

---

### Post by bluevoodoo1 on 2006-06-09
[QUOTE=seth0x2b]Try [http://glchess.sourceforge.net/](http://glchess.sourceforge.net/)

Cheers[/QUOTE]


That's great! Thanks.

---

### Post by delfick on 2006-06-09
thanx Niamor, i got the sdl thing now...

my question now is how do i install it? The readme says something about typing 'scons configure' in the terminal but when i do that it says

```
scons: *** No SConstruct file found.
File "/usr/lib/python2.4/site-packages/SCons/Script/__init__.py", line 870, in _main

```

i have absolutely no idea what i'm doing :'(

---

### Post by Niamor on 2006-06-09
Hmmm I believe you took the source version ?

You should download the Linux binaries (tar.gz) version, also on the download page. Then you only have to click on pouetchess in the bin folder.

If you have the same problem as me, clicking  doesn't start the game but my resolution is all messed up, you should open a terminal and start the game with ./pouetchess if you are in the directory of bin or /home/yourname/bin/pouetchess

It's a bit weird but this way it works, haven't played much but the AI seemed really slow.

Have fun :p

---

### Post by charlieg on 2006-06-09
[QUOTE=delfick]that looks fantastic!

the only problem is that i'm fairly new to linux and have no idea where to get this SDL and SDL-image it says it needs...

you don't have to help me but if u do....thnx

:D[/QUOTE]
Try Synaptic.  Search for libsdl and install what makes sense.

---

### Post by delfick on 2006-06-09
yay it works...

thankyou for all ur help!

---

### Post by milwac on 2006-08-02
I downloaded both the glchess and python packages and typed in the command :

dpkg -i python2.4-gtkglext1_*_i386.deb glchess_*_all.deb

However I encountered the following error message:

Selecting previously deselected package python2.4-gtkglext1.
(Reading database ... 77703 files and directories currently installed.)
Unpacking python2.4-gtkglext1 (from python2.4-gtkglext1_1.1.0-1_i386.deb) ...
Selecting previously deselected package glchess.
Unpacking glchess (from glchess_0.9.5-1_all.deb) ...
dpkg: dependency problems prevent configuration of python2.4-gtkglext1:
 python2.4-gtkglext1 depends on libgtkglext1 (>= 1.0.6); however:
  Package libgtkglext1 is not installed.
dpkg: error processing python2.4-gtkglext1 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of glchess:
 glchess depends on python2.4-gtkglext1; however:
  Package python2.4-gtkglext1 is not configured yet.
dpkg: error processing glchess (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-gtkglext1
 glchess

How should I fix this?..please help!

---

