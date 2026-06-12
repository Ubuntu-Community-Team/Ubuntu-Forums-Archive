---
title: "No &quot;window&quot; around app in gnome/gutsy."
date: 2007-11-22
forum: Desktop Environments
---

### Post by MarkLori on 2007-11-22
I'm not sure about the proper terminology but normally I have a "window" that my app pops up in.  For instance, if I open Firefox there are no tools at the top right to close, minimize, etc., no way to grab the sides and resize it.   I can maximize by using the F11 key.  When I do it fills the whole screen including the top and bottom gnome menu bars and seems to refresh periodically, causing the screen to black out and come back.  

I am running a Dell Optiplex GX 240 with an nVidia card.  I did a clean install, enabled the nVidia driver, ran updates, and have run automatix to install some stuff.  That's it so far.

Any help is greatly appreciated.

Mark

---

### Post by Telecaster72 on 2007-11-23
Hi Mark
 I assume you mean the "window decorations", there is many threads on them dissapearing while using compiz.

I just went into the restricted drivers manager, uninstalled the nvidia driver and then reinstalled it again.
It used to work for me anyway, i have a GeForce 3 ti200 card btw.
Good luck and if this does not work do a search on window decorations.

---

### Post by bartos on 2007-11-23
Mine always disappeared when using emerald themes. I just use metacity for window decorations.
Install the Compiz fusion tray icon to switch easily.

[http://ubuntuforums.org/showthread.php?p=3163821](http://ubuntuforums.org/showthread.php?p=3163821)

---

### Post by Telecaster72 on 2007-11-24
Also make sure that window decorations are enabled in the advanced desktop settings!

---

### Post by MarkLori on 2007-11-24
Thanks for the help guys!  Somehow the visual effects setting had no selection at all.  I know I had looked there before and it wasn't like that.  Oh well.  Onward...

Thanks for the help!

---

### Post by chronographer on 2007-11-24
If you use compiz fusion, like I do, you may need a certain comand to magically get window decorations going!

I use a startup script to load compiz and decorations on startup.

if you copy and paste these lines, one at a time into your terminal, see if it fixes things:
> 
compiz --replace --only-current-screen &
gtk-window-decorator --replace &

If this works (and you want to use compiz) then make a script called something like compiz.sh and store it somewhere like /home/<YOUR USERNAME>/.gnome2/nautilus-scripts
(you can do this by typing "gedit /home/<USERNAME>/.gnome2/nautilus-scripts/compiz.sh") and put this into it:

> 
#!/bin/bash
compiz --replace --only-current-screen &
gtk-window-decorator --replace &

Now you need to make it executable, which I can never do via command line, so I right click on the compiz.sh script and go to permissions and check 'allow executing...' now you can add it to your startup by going to System - preferences - sessions - add, and point it to that file.

---

