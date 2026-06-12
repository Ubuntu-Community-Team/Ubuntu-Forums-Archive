---
title: "Using multimedia keys with XMMS"
date: 2006-08-06
forum: Desktop Environments
---

### Post by srunni on 2006-08-06
Hey,

I used the "Keyboard Shortcuts" utility in GNOME (System -> Preferences -> Keyboard Shortcuts) to set multimedia keys on my keyboard to play, pause, stop, etc., but they don't work by default in XMMS. Does anyone know how to fix this?

---

### Post by srunni on 2006-08-07
Any ideas?

---

### Post by fantan on 2006-08-07
Hi,

In my system (Dapper 6.06 + Gnome desktop) also I use multimedia keys.
The type of my keyboard is Genius Comfy KB16-M with 16 multimedia keys.
But for the control of the XMMS I use the xbindkeys and xbindkeys_config packages, in which you can configure same shortcuts for controling XMMS.
The commands you should write in xbindkeys_config are: 

Rewind      xmms --rew
Play/Pause  xmms --play-pause
Stop        xmms --stop
Forward     xmms --fwd
and you should select the proper keys to these commands too.

At the same time you have to switch off these multimedia keys in the System->Preferences->Keyboard shortcuts. This is very important to avoid double control of these keys.
You can use the xbindkeys program to setup any shortcut you like too.

fantan

---

### Post by srunni on 2006-08-07
I understand that you can manually keybind (I have done this before in KDE), but I would rather have this integrated with Ubuntu, instead of relying on more 3rd party programs. Is there any way to make GNOME associate the shortcuts I've specified to it with certain actions in programs?

---

### Post by BaroldGene on 2008-02-28
I'm having the same problem.  I want to keep the keys bound to what they are bound to in Gnome, I just want them to affect XMMS also.  I'm currently trying to install XMMS2 to see if that does anything.

---

