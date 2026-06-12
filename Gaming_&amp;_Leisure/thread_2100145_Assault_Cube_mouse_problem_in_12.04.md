---
title: "Assault Cube mouse problem in 12.04"
date: 2012-12-31
forum: Gaming &amp; Leisure
---

### Post by iowabeakster on 2012-12-31
The mouse wheel becomes unresponsive if the mouse is moving (turning) simultaneously.  In terms of game play... you can't switch weapons while moving the mouse.  You must stop moving the mouse in order to be able to switch weapons.

I heard that this was a known bug and an easy fix... but that was months ago.  I forgot where I heard this.

I finally got around to updating my OS to 12.04.  The problem happens both in Ubuntu and Xubuntu.

---

### Post by iowabeakster on 2012-12-31
I found it... for anyone else who might want to know...

> This is a problem specific to Linux, and it's not only highly annoying, but it will also keep you from playing well. It's even worse than the pistol firing problem. Luckily, there's a known solution.
Open assaultcube.sh, and after #!/bin/sh, add the following lines:
```
export SDL_VIDEO_X11_MOUSEACCEL="1/1/1"
export SDL_VIDEO_X11_DGAMOUSE=0
```


---

