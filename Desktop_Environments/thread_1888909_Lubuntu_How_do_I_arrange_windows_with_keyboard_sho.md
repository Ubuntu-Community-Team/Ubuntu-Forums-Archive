---
title: "Lubuntu: How do I arrange windows with keyboard shortcuts?"
date: 2011-11-30
forum: Desktop Environments
---

### Post by iveand on 2011-11-30
I have been testing with Lubuntu and have found it really pleasant. However, I cannot find an answer for one essential (for me) feature: being able to arrange windows with keyboard shortcuts.

In Ubuntu this is done with the "Grid" plugin in "compizconfig-settings-manager". Unity uses this as well for window arranging.

I am not interested in the "drag to the left to take up 1/2 the screen", but rather just the "hit some key combo" to put the active window to the left 1/2 of the screen, for example.

I found this entry in "askubuntu" asking a very similar question:

[http://askubuntu.com/questions/15198/is-there-a-way-to-make-openbox-behave-like-the-compiz-grid-plugin]("http://askubuntu.com/questions/15198/is-there-a-way-to-make-openbox-behave-like-the-compiz-grid-plugin")

But it seems the "answer to this question", namely pyTile ([http://sourceforge.net/projects/pytile/]("http://sourceforge.net/projects/pytile/")), doesn't do what I would like it to do. I don't want to tile all current windows, I want to resize one window at a time as I specify (left, right, top, center, bottom, 1/2, 2/3, 1/3, etc.). And I would prefer to do so with the keyboard.

I think it possible to install compiz in Lubuntu, but this seems like "overkill" for this one feature (Grid keyboard shortcuts). Any help out there? It would REALLY MAKE MY DAY!!!

---

### Post by searchfgold6789 on 2011-11-30
Since lxde does not yet have its own thing for windows effects, which is what you'd need to activate the effect, it is unlikely that you'll be able to get this desired effect without installing one, like Compiz.

---

### Post by iveand on 2011-11-30
Thanks for the quick reply.

I am certainly not opposed to compiz.  For me the grid effect is well worth it.  My machine is up to the task (I appreciate that many using lxde are doing so because of performance / speed / simplicity issues).

If I install compiz and ccsm is that adequate?  Will compiz load by default? Or is there some tweaking needed to let lubuntu know that compiz should be used by default on login for window effects?

iveand

---

### Post by searchfgold6789 on 2011-11-30
Compiz should be loaded at startup, actually the last time I tried installing it it was activated immediately after installing. It should work all the time. Some people are having troubles with rebooting and finding that compiz isn't there, but this is solved if when you shutdown you "save your seesion" (there is an option for this in LXDE, I don't know if it's in the settings manager or if it's in the shutdown options menu itself.) If it still doesn't work, then just add this line to your ~/.bash-login file:```
compiz --replace &
```

---

### Post by LewisTM on 2011-11-30
If you want to keep your window manager and emulate the grid fucntionality, you can try [PyWO - Python Window Organizer]("http://code.google.com/p/pywo/"). It can be controlled with the keyboard.

Cheers!:D

---

### Post by iveand on 2011-11-30
> **searchfgold6789 said:**
> Compiz should be loaded at startup, actually the last time I tried installing it it was activated immediately after installing. It should work all the time. Some people are having troubles with rebooting and finding that compiz isn't there, but this is solved if when you shutdown you "save your seesion" (there is an option for this in LXDE, I don't know if it's in the settings manager or if it's in the shutdown options menu itself.) If it still doesn't work, then just add this line to your ~/.bash-login file:```
compiz --replace &
```

OK, a few issues here.  I installed compiz.  It isn't starting well.  If I open a terminal an issue the command suggested (compiz --replace &), all open windows go crazy, the bottom LXDE panel turns off, and then it settles down. I get errors in the terminal indicating "theme parsing errors". All "hot keys" don't work anymore (ctrl + alt + t for terminal, "super" for menu, etc.), Workspace viewer complains, etc. etc.

I am thinking throwing compiz on top of lxde is causing some conflicting issues that I would be tracking down for a while... I'll see if the python tool referenced below will work.

Otherwise suggestions of "xmonad" or "awesome" have been suggested: from what I can tell, these options are going to need some "from scratch setup".  I am not opposed to that, but I am hoping to pass on these same techniques to beginners with Lubuntu that are not going to want to be doing any of that.  Maybe I have the wrong impression, but those 2 tools don't seem like good options for me at this stage (maybe later if I remain "desperate").

---

### Post by iveand on 2011-11-30
> **LewisTM said:**
> If you want to keep your window manager and emulate the grid fucntionality, you can try [PyWO - Python Window Organizer]("http://code.google.com/p/pywo/"). It can be controlled with the keyboard.

Cheers!:D

Oh my goodness am I impressed. Very simple, very effective. Even compiz grid has been "broken" in 11.10 in that it doesn't work to do anything but "half screen" (so, hit "left" and it goes to half, but hit it again and nothing further happens: so no 1/3, 2/3, 1/4 etc).

PYWO IT IS!!!! Thanks for the lead.  Highly recommended to anyone finding this thread.

---

