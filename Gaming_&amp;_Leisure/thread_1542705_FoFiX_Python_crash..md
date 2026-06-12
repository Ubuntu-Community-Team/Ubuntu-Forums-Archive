---
title: "FoFiX Python crash."
date: 2010-07-30
forum: Gaming &amp; Leisure
---

### Post by Selim873 on 2010-07-30
Hi everybody!  I have a question because FoFiX is always crashing...  The original Frets on Fire runs fine, but it sucks, FoFiX is what I've always played when I was on Windows because it supported flawless drums... The drums work, but I have this weird crash when I want to configure it. I'm guessing it has something to do with GL because that's being shown in the error.  My terminal logged the whole situation so is there something that I need to install?  Thanks for reading this.  :D

I know it says Netbook but that shouldn't be a problem because my desktop that has a 2-5 years older Intel Chipset runs it just fine (It's using Windows XP)! Actually, my netbook has better specs except for CPU, that has nothing to do with GL.  Just had to mention that before people start making false assumptions just because I'm using Intel.

:guitar:

```
ty@Ty-NETBOOK:~$ cd games
ty@Ty-NETBOOK:~/games$ cd fofix
ty@Ty-NETBOOK:~/games/fofix$ cd src
ty@Ty-NETBOOK:~/games/fofix/src$ python FoFiX.py
SDL_JoystickNumHats value:0:
Traceback (most recent call last):
  File "/home/ty/games/fofix/src/GameEngine.py", line 1047, in run
    return self.mainloop()
  File "/home/ty/games/fofix/src/GameEngine.py", line 1022, in main
    self.view.render()
  File "/home/ty/games/fofix/src/View.py", line 216, in render
    layer.render(self.visibility[layer], layer == self.layers[-1])
  File "/home/ty/games/fofix/src/Menu.py", line 468, in render
    tipFont.render(choice.tipText, (self.tipScroll, self.tipY), scale = tipScale)
  File "/home/ty/games/fofix/src/Font.py", line 179, in render
    t.loadSurface(s, alphaChannel = True)
  File "/home/ty/games/fofix/src/Texture.py", line 122, in loadSurface
    self.loadRaw(surface.get_size(), string, GL_RGBA, 4)
  File "/home/ty/games/fofix/src/Texture.py", line 157, in loadRaw
    gluBuild2DMipmaps(self.glTarget, components, w, h, format, GL_UNSIGNED_BYTE, string)
  File "/usr/lib/pymodules/python2.6/OpenGL/error.py", line 194, in glCheckError
    baseOperation = baseOperation,
GLError: GLError(
    err = 1281,
    description = 'invalid value',
    baseOperation = gluBuild2DMipmaps,
    cArguments = (
        GL_TEXTURE_2D,
        4,
        4096,
        64,
        GL_RGBA,
        GL_UNSIGNED_BYTE,
        '\xff\xff\xff\x00\xff\xff\xff\x00\xff...,
    ),
    result = 0
)
Fatal Python error: (pygame parachute) Segmentation Fault
Aborted
ty@Ty-NETBOOK:~/games/fofix/src$ 

```

---

