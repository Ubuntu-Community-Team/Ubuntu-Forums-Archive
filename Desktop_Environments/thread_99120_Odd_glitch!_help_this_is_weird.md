---
title: "Odd glitch! help this is weird"
date: 2005-12-04
forum: Desktop Environments
---

### Post by Kanephan on 2005-12-04
It's the strangest thing. Its happened with a few executable files with the SH icons (I'm not sure what to call them). I can only execute them in their folders. That is to say, links to the SH that I place on the desktop won't work. The program either won't open, or will flash the terminal or something and shut down. It only works problem free if I find the folder and execute it from there.

Anyone know why this is? It's really inconveniant. Id like my desktop shortcuts to serve a purpose :(

---

### Post by xmastree on 2005-12-05
I'm not sure why, but the desktop does behave differently. For example, I have a nautilus script for rotating images. If the image is on the desktop then it doesn't work.

Why not put the scripts (that's probably what they are) in a folder and create a launcher on the desktop for them?

---

### Post by Kanephan on 2005-12-05
Well I tried to create a launcher for the top bar of gnome, but that had the same result.

This has happened with America's Army, where the program didnt start at all unless it was run from the folder. But the thing I'm talking about now is the Last.Fm player. 

As soon as I pick a radio, the thing shuts down by itself. That is only if it is run from anywhere but the desktop, the top bar of gnome included.

I'm not sure if making a launcher on the desktop itself would have a different result. I doubt it, but I can try. I don't know how to do that though....

---

### Post by xmastree on 2005-12-05
well, right click on the desktop, and select **create launcher** Name can be anything you like, Command is what you would type to run it.

---

### Post by ZephyrXero on 2005-12-05
I have had similar crashing problems with it. I think it must have something to do with the sound server (Alsa/esd) being busy or something...because it doesn't crash till you start trying to play something. Yet today it works for some reason... I downloaded the binary and extracted it in my home directory, but hopefully it'll be in the Dapper repositories. I've added it as a [candidate on the wiki]("https://wiki.ubuntu.com/UniverseCandidates")... If any of you would like to see it added too, please leave comments following the page's guidelines ;)

---

### Post by cwaldbieser on 2005-12-05
[QUOTE=Kanephan]It's the strangest thing. Its happened with a few executable files with the SH icons (I'm not sure what to call them). I can only execute them in their folders. That is to say, links to the SH that I place on the desktop won't work. The program either won't open, or will flash the terminal or something and shut down. It only works problem free if I find the folder and execute it from there.

Anyone know why this is? It's really inconveniant. Id like my desktop shortcuts to serve a purpose :([/QUOTE]
Sometimes a script relies on another file that is relative to where the main file is.

Try creating a script like this:
```

#!/bin/bash

cd /path/to/other/script
./otherscript

```
Make that script executable, and then make the shortcut to that script instead.

---

