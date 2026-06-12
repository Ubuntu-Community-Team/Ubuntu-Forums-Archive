---
title: "Tile all open windows with hotkey?"
date: 2009-02-04
forum: Desktop Environments
---

### Post by jnewl on 2009-02-04
I don't think they exist anymore, but earlier versions of Windows offered the ability to Tile and Cascade all the open windows on your desktop via hotkeys. Those functions weren't useful to me at the time, but some stuff I'm doing now would be made a whole lot easier if I could Tile everything in one shot like that. Does anyone know if that's even possible in Ubuntu and, if so, how to go about it? 

I already checked System->Preferences->Keyboard Shortcuts and didn't see anything there.

---

### Post by Sorivenul on 2009-02-04
I'm assuming you are using the "default" GNOME environment from Ubuntu. 

If that is the case [this guide]("http://ubuntuforums.org/showthread.php?t=470160") may be of help, though a bit dated; I believe it uses [wmtile]("http://freshmeat.net/projects/wmtile/"). You could easily bind a key to the "tile -v -h" command instead of creating a launcher in the panel, though either method should work. 

Otherwise [devilspie]("http://www.burtonini.com/blog/computers/devilspie") and [this guide]("http://foosel.org/linux/devilspie") may be a good route. 

Another neat program to help, though not specifically with tiling/cascading is [Windowgrouper]("http://windowgrouper.sourceforge.net/").

Hope this helps!

---

### Post by jnewl on 2009-02-04
Thanks! Looks like wmtile will work (the link you gave is dead, though; I found it via Google). And thanks for Devil's Pie as well. That might come in handy :D

---

### Post by jnewl on 2009-02-04
Oops. Actually, wmtile doesn't quite do what I'm looking for. If I'm understanding correctly, it will only tile windows either horizontally or vertically. But in the old Windows program (3.1, IIRC) I seem to remember it making various patterns based upon the number of windows. With nine windows, for example, you got a Tic-Tac-Toe arrangement. That's the kind of thing I'd like to have, rather than nine thin windows stacked vertically up the screen.

Do you or anyone else know of any way to do this?

---

### Post by zhocchao on 2009-02-04
try this:

[http://ubuntuforums.org/showthread.php?t=1034246](http://ubuntuforums.org/showthread.php?t=1034246)

---

### Post by jnewl on 2009-02-04
Thanks! wmctrl looks like it will at least allow me to hardcode behavior for exactly X number of windows, so that's much better than nothing. Unfortunately, I don't understand the code, nor do the two scripts (tileprio.sh, takeplace.sh) seem to work properly for me. I'm using the default Ubuntu Gnome desktop with compiz.

I successfully installed wmctrl, but when I run tileprio.sh I get an error:

[INDENT]tileprio.sh: 11: Syntax error: "(" unexpected (expecting "fi")[/INDENT]

My meager programming skills lead me to think there's an unassociated left parenthesis in line 11. But I read through the whole file and didn't find anything that stood out to me, so I don't know what's up.

Alternately, when I run takeplace.sh it resizes the terminal window and places it in a specific spot on my desktop. Although I have gedit, two web browsers, and a file browser window open as well, they are not affected. 

So takeplace.sh seems to sort of be working, but not as robustly as I'd like. Here's what I'm looking for: I'd like to have a script for up to nine windows, without regard for what programs are running in them, arranged in tac-tac-toe style at 1680x1050 resolution. 

Are there some simple modifications I can make to the file(s) to make either of them do what I want?

Thank you very much! I think I'm getting closer :D

---

### Post by IceReaver75 on 2009-02-05
I'm not sure if this is what your looking for but if your using gnome with compiz running you could just use the scale option in compiz-setting-manager.  Just set the initiate window picker to use a screen edge or keyboard key combo to start and it will scale all open windows you have open into one window.  If you use the screen edge option you can use the mouse to pick what window to go to.  Looks like this.

---

### Post by zhocchao on 2009-02-05
@jnewl

takeplace.sh is meant as a "minimizing" script, so I can see the desktop Icons. It is not ready yet. (By now it's going Python)
I downloaded tileprio, which is doing exactly what you want, it works on my notebook without syntax errors. Did you change anything before starting it. Maybe accidental.

Dont do:
 sh tileprio.sh

just:
 ./tileprio.sh

or create a starter or double click (allow executing file as programm)

---

### Post by jnewl on 2009-02-06
Ch-ching! Score! Thanks, zhocchao. I was trying to start the script with sh. That was the problem. 

And thank you also, IceReaver. I'm going to check out the compiz scale function and see if that's useful for me as well.

Right on. You guys made my day! :D

---

### Post by strungoutfromtheroad on 2009-02-27
This is what you are looking for...[http://ubuntuforums.org/showthread.php?t=1054471&highlight=tile+windows](http://ubuntuforums.org/showthread.php?t=1054471&highlight=tile+windows)

---

### Post by jnewl on 2009-02-27
Yep. That's exactly what I've been looking for. Works like a charm! Thanks so much!

Small correction for anyone else who might be reading this + the linked thread: the package in Synaptic is actually called compiz-fusion-plugins-unsupported, not compiz-unsupported-plugins. 

Instructions: Just install it, go into System -> Preferences -> CompizConfig Settings Manager, press Window Management and choose Tile. If it complains that it needs to resolve a conflict, resolve it in Tile's favor (unless you specifically need the other thing to work; I didn't even know what it did). Now you're done. If you want to change the key bindings or window animations, press Tile. Otherwise, it's Shift-Super (i.e. Windows key)-a to tile, Shift-Super-s to cascade, Shift-Super-z to restore to the original configuration, and Shift-Super-x to "toggle tile," which I'm not exactly sure about.

---

