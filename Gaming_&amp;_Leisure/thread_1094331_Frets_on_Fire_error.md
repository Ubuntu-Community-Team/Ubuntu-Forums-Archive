---
title: "Frets on Fire error"
date: 2009-03-12
forum: Gaming &amp; Leisure
---

### Post by TwistedNail on 2009-03-12
Downloaded it, experimented with video settings and after I putted resolution on 640x*** (window mode), when I lounch it through terminal it opens and closes after 1sec...

Terminal:
> reinis@Tn:~$ fretsonfire
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
reinis@Tn:~$ 


Any suggestions?? Please help :(

---

### Post by TwistedNail on 2009-03-12
Problem solved..
Searched for Frets on Fire FAQ.

---

