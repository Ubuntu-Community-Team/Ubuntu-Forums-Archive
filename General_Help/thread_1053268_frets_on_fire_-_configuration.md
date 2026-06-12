---
title: "frets on fire - configuration"
date: 2009-01-28
forum: General Help
---

### Post by balta on 2009-01-28
hi everybody

i just installed frets on fire thought the "add remove" option and everything looked fine

BUT i'm a fool and before even trying to play the game i went in options a tried to change the screen res raising it to 1280x1024 (my screen actual res)
the game crashed and crashes everythime i try to run even after the "complete" removal and the re installation it 

this is the terminal error report:
```

~$ fretsonfire
Traceback (most recent call last):
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 348, in run
    return self.mainloop()
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 340, in main
    self.view.render()
  File "/usr/share/games/fretsonfire/game/View.py", line 183, in render
    layer.render(self.visibility[layer], layer == self.layers[-1])
  File "/usr/share/games/fretsonfire/game/Menu.py", line 164, in render
    self.engine.view.setOrthogonalProjection(normalize = True)
  File "/usr/share/games/fretsonfire/game/View.py", line 147, in setOrthogonalProjection
    viewport[3] - viewport[1], viewport[1], -100, 100);
  File "/usr/lib/python2.5/site-packages/OpenGL/error.py", line 193, in glCheckError
    baseOperation = baseOperation,
GLError: GLError(
        err = 1281,
        description = 'invalid value',
        baseOperation = glOrtho,
        cArguments = (0, 1, 0.0, 0, -100, 100)
)

```

i don't know why even after reinstalling it doesn't work, maybe it remembers the old settings, where i may found them and cancel them forever?

or maybe the problem is another one...

please someone help me i feel like i just "killed" a working game

---

### Post by jerome1232 on 2009-01-28
Check in your home directory for the configuration file and edit the resolution by hand, I've done it before I think it was ~/.fretsonfire you should be able to find it.

--edit--- hit ctrl+h to view hidden files/folders

---

### Post by balta on 2009-01-28
thanks mate it just simply worked perfectly

i'm going to rock my keyboard now

thanks

---

