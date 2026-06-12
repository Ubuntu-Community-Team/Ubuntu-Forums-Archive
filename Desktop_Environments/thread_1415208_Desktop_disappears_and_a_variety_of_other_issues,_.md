---
title: "Desktop disappears and a variety of other issues, screen tearing, resizing"
date: 2010-02-24
forum: Desktop Environments
---

### Post by Kenjitamura on 2010-02-24
The bug im going to report first is the most recent one to appear, whenever i right click on an item on the desktop and try to go to properties all the icons on my dekstop disappear and I can no longer right click on the desktop space.  This problem doesn't go away until I restart X.  I can still access all the files by going to the toolbar under places desktop and can even access their properties from there.  The next issue might be related in some way, whenever i restart my computer the ubuntu loading screen only takes up 1/4 of the screen (top left), also the i can see what looks like a piece of the ubuntu symbol to the far right of the screen at the exact same height on the screen.

I use an ati video card and when I try to maximize a window after its been minimized it takes about 2 seconds to respond, the workaround I found for this was disabling composite effects in the xorg.  There are still video issues though, when I try to play videos in mplayer i get bad horizontal tearing across the screen in several places during parts of high motion.  I installed compiz config and turned on vsync but that didnt fix the problem, i also turned vsync on in the video card.  I heard mplayers gui could be the problem so I installed smplayer and have even tried the settings postprocessing and direct render but no dice, same amount of tearing.  This tearing has been tested in X11, XV, and gl2 all three have it.

At first I hadn't installed the ati proprietary drivers from their website I just used EnvyNG, last night I uninstalled those, created the debs, and installed them according to the guide even configuring the xorg.  The drivers work but all the problems still persist.  I guess there is one last clue, by default mplayer would try to load videos with xmga and i'd get an error resulting in only audio playing, checking vo help xmga isn't listed as a playback option.

The video card is an HD 4650 if that's of any help.  Any suggestions are appreciated.

---

### Post by Kenjitamura on 2010-02-24
Well I did a variety of attempts but what has solved most problems is as follows.  1.  The desktop disappearing was from nautilus crashing and after i deleted the home folder as described in [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/505860](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/505860) nautilus stopped crashing.  2.  The video problems just still appear to be faulty driver (i.e. only part of loading screen appearing).  3.  I FINALLY got playback without tearing by installing VLC, at first VLC was still tearing with default output but when I switched it to OpenGL for the first time i could watch a scene that always tore without any issues.  Odd how switching to opengl didn't fix it in mplayer though.

---

