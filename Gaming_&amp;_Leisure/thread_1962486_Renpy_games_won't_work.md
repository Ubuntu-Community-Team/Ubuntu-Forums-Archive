---
title: "Renpy games won't work"
date: 2012-04-21
forum: Gaming &amp; Leisure
---

### Post by burdebc on 2012-04-21
For some reason none of my renpy games don't work.  I got the following traceback from the game moonlight.  I will gladly give any more information that is needed, thanks.

I'm sorry, but an exception occured while executing your Ren'Py
script.

error: Unable to open a console terminal

After initialization, but before game start.

-- Full Traceback ------------------------------------------------------------

  File "/home/burdebc/Downloads/visual-novels/moonlight-2.0-linux-x86/renpy/bootstrap.py", line 247, in bootstrap
    renpy.main.main()
  File "/home/burdebc/Downloads/visual-novels/moonlight-2.0-linux-x86/renpy/main.py", line 298, in main
    game.interface = renpy.display.core.Interface()
  File "/home/burdebc/Downloads/visual-novels/moonlight-2.0-linux-x86/renpy/display/core.py", line 1068, in __init__
    self.display = Display(self)
  File "/home/burdebc/Downloads/visual-novels/moonlight-2.0-linux-x86/renpy/display/core.py", line 674, in __init__
    pygame.display.init()
error: Unable to open a console terminal

After initialization, but before game start.

Ren'Py Version: Ren'Py 6.8.1a

---

