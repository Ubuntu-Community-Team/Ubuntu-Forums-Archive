---
title: "Frets on Fire not working"
date: 2007-12-15
forum: Gaming &amp; Leisure
---

### Post by azurelight1337 on 2007-12-15
alland@allan-desktop:~$ fretsonfire
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Traceback (most recent call last):
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 346, in run
    return self.mainloop()
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 336, in main
    done = Engine.run(self)
  File "/usr/share/games/fretsonfire/game/Engine.py", line 139, in run
    self._runTask(task)
  File "/usr/share/games/fretsonfire/game/Engine.py", line 130, in _runTask
    task.run(ticks)
  File "/usr/share/games/fretsonfire/game/Resource.py", line 166, in run
    loader.finish()
  File "/usr/share/games/fretsonfire/game/Resource.py", line 85, in finish
    self.onLoad(self.result)
  File "/usr/share/games/fretsonfire/game/Dialogs.py", line 383, in songListLoaded
    self.updateSelection()
  File "/usr/share/games/fretsonfire/game/Dialogs.py", line 418, in updateSelection
    self.selectedItem  = self.items[self.selectedIndex]
IndexError: list index out of range
Traceback (most recent call last):
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 346, in run
    return self.mainloop()
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 338, in main
    self.view.render()
  File "/usr/share/games/fretsonfire/game/View.py", line 183, in render
    layer.render(self.visibility[layer], layer == self.layers[-1])
  File "/usr/share/games/fretsonfire/game/Dialogs.py", line 696, in render
    item  = self.items[self.selectedIndex]
IndexError: list index out of range


Help?

---

### Post by piratesmack on 2007-12-16
open the synaptic package manager and search "frets on fire"

There should be a package called "fretsonfire-songs-sectoid"

Install it

---

### Post by Goofee691 on 2007-12-16
if you are useing a ati card this should get rid of the Xlib: extension "XFree86-DRI" missing on display ":0.0".
[http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+radeon+xpress+200m](http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+radeon+xpress+200m)

but right now im stuck here


sean@NUM4Php:~$ fretsonfire
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 166, in __init__
    self.svg = SvgContext(geometry)
  File "/usr/share/games/fretsonfire/game/Svg.py", line 78, in __init__
    self.setGeometry(geometry)
  File "/usr/share/games/fretsonfire/game/Svg.py", line 91, in setGeometry
    geometry[2], geometry[3])
  File "/usr/share/games/fretsonfire/game/DummyAmanith.py", line 42, in SetViewport
    glViewport(x, y, w, h)
ctypes.ArgumentError: argument 3: <type 'exceptions.TypeError'>: wrong type
sean@NUM4Php:~$

---

### Post by azurelight1337 on 2007-12-17
Well, I got it working but installing the SourceForge one...

But now it runs REALLY slow, even with settings turned down on lowest... Audio doesn't lag though.

---

### Post by werewolfzx8 on 2007-12-17
> **azurelight1337 said:**
> Well, I got it working but installing the SourceForge one...

But now it runs REALLY slow, even with settings turned down on lowest... Audio doesn't lag though.

Have you tried messing around with the screen resolution?

---

### Post by grogger13 on 2007-12-20
Mine wont work either, it starts fine but when i enter into a song it cuts out and shuts down.
```

mike@mikelap:~$ fretsonfire
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Traceback (most recent call last):
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 346, in run
    return self.mainloop()
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 338, in main
    self.view.render()
  File "/usr/share/games/fretsonfire/game/View.py", line 183, in render
    layer.render(self.visibility[layer], layer == self.layers[-1])
  File "/usr/share/games/fretsonfire/game/GuitarScene.py", line 352, in render
    SceneClient.render(self, visibility, topMost)
  File "/usr/share/games/fretsonfire/game/Scene.py", line 284, in render
    self.render3D()
  File "/usr/share/games/fretsonfire/game/GuitarScene.py", line 224, in render3D
    self.stage.render(self.visibility)
  File "/usr/share/games/fretsonfire/game/Stage.py", line 344, in render
    self.scene.renderGuitar()
  File "/usr/share/games/fretsonfire/game/GuitarScene.py", line 227, in renderGuitar
    self.guitar.render(self.visibility, self.song, self.getSongPosition(), self.controls)
  File "/usr/share/games/fretsonfire/game/Guitar.py", line 435, in render
    glScale(-1, 1, 1)
NameError: global name 'glScale' is not defined


```

---

### Post by John164918a on 2008-03-02
I have precisely the same problem.

If you run:

fretsonfire -v

In the first few lines for me it says that the package python-pyvorbis isn't installed and then that 'PyAmanith' isn't installed. I've downloaded the vorbis one and now it only complains about PyAmanith which isn't in the repository. I think finding this and installing it may be the key.

---

### Post by John164918a on 2008-03-05
Ladies and gentlemen! I have the solution!

At least it worked for me:
The current version is 1.2.512

Download Frets On Fire version 1.2.451 instead.


:guitar:

---

