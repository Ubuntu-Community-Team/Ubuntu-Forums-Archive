---
title: "Frets on fire help"
date: 2008-03-29
forum: Gaming &amp; Leisure
---

### Post by spider3000 on 2008-03-29
Hello Ubuntu users!

I've followed [this guide]("http://gaming.gwos.org/doku.php/guides:32bit:fretsonfire") to install Frets on fire but I've run across some problems.

The first problem is when I start a song, the last screen I can see is something like "loading guitar" (not sure what it said exactly) before the application closes and I'm on the desktop again. I've since run the game from the console, and this is the output:

sh FretsOnFire

Traceback (most recent call last):
  File "src/GameEngine.py", line 350, in run
  File "src/GameEngine.py", line 342, in main
  File "src/View.py", line 183, in render
  File "src/GuitarScene.py", line 352, in render
  File "src/Scene.py", line 158, in render
  File "src/GuitarScene.py", line 224, in render3D
  File "src/Stage.py", line 344, in render
  File "src/GuitarScene.py", line 227, in renderGuitar
  File "src/Guitar.py", line 467, in render
NameError: global name 'glScale' is not defined

I hope someone knows what I have to do to fix it. Also, I have compiz disabled while I run the game.

The second issue I have with Frets on fire is when I change the graphics settings and click on apply, the game crashes and all I see is black. I can't get to my desktop, and all I can do is press Ctrl+Alt+Backspace. Does anyone know how I can change the settings without it crashing? or is there a config file I can manually edit?

My last question is just an extra thing I was wondering. Is there any keyboard combination to switch to another program or the desktop when I'm inside a game? In Windows there's Alt+Tab and Ctrl+Alt+Delete and a couple of others, but they don't seem to work in Ubuntu. Any ideas are appreciated.


Thanks for any help!
~Ubuntu / Linux newbie~

---

