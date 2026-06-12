---
title: "Resolution issues (Nvidia card)"
date: 2009-05-14
forum: General Help
---

### Post by Bandit224 on 2009-05-14
In short, FreeDroidRPG used to work, changed resolution size, and now it doesn't.  I need to know how I can change the in-game resolution back to what it was.

running 9.04 Jaunty, downloaded and played FreeDroidRPG from Synaptic Packages.  It worked for several days until I tried changing the resolution size in-game.  Now, when launching FreeDroidRPG, the looks like the program loads, but the screen remains on the desktop.  I can't find FreeDroid's processes running in System Monitor, so the program isn't running.  I tried completely removing the package through Synaptic, and installing a fresh copy, same thing happens.

I strongly think that the problem is the change in the resolution size, due to how NVidia handles the resolutions.  

1)  What is the default directory that Synaptic installs the programs to?  I found a folder that has various files, but they seem to be only shortcut links.

2)  How do I change the in-game settings without loading the game itself?

---

### Post by pandanuma on 2010-07-16
open in terminal with:  freedroidRPG -w
that should open game in a window not fullscreen

also...
freedroidRPG -r99  will show you available screen resolutions

and check out:  freedroidRPG --help

---

