---
title: "Warcraft 3 - opengl command in wine"
date: 2005-11-21
forum: Gaming &amp; Leisure
---

### Post by the_purulent on 2005-11-21
I got wc3tft to install perfectly fine under wine.  When I launch the game it loads properly, I see the intro video and then I get a blank black screen.

I've read the using the -opengl switch may help.  I am just unsure how to add it to my launcher command.

could someone give me the command to launch a game in wine with full opengl suport?

---

### Post by Perfect Storm on 2005-11-21
I think it should look like this (I'm not using wine myself).

wine "/blah/blah/blah/XXXXXXXXXXXXX.exe" -opengl

---

### Post by the_purulent on 2005-11-21
Well, had I known it was as simple as all that I'd have had it working by now. :)
I guess I just assumed there would be more commands or options I would need to enter.
Thanks!
-clay

---

### Post by Iotos on 2009-06-03
I can confirm it works; the -opengl switch made a world of difference. Where it barely ran before, it now performs just as well my native windows box. In fact, it might very well be bias, but it seems that applications with an opengl mode seem to look better than they do in directx mode, even in windows.

Wine: 1.1.22
ATI Driver Version (did not work until I updated): 8.1.85 (part of catalyst version 9.3)
launcher format (just the default with -opengl tacked onto the end):

env WINEPREFIX="/home/<yourname>/.wine" wine "C:\Program Files\Warcraft III\Frozen Throne.exe" -opengl

---

### Post by wingnux on 2009-06-03
Please, post wine-related questions on the appropriate forum [http://ubuntuforums.org/showthread.php?t=624170](http://ubuntuforums.org/showthread.php?t=624170)

This thread will be moved soon.

---

### Post by wolfyking2 on 2009-06-03
or locked.  Necromancy :)

    ///
    |---------------
    | ---------------
    |-----------------
    |  --------------
    \\\

---

### Post by hikaricore on 2009-06-03
4 year old thread..

---

