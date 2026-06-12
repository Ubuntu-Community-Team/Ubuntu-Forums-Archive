---
title: "xmame compile (linking) error - Help me please!"
date: 2007-12-01
forum: Gaming &amp; Leisure
---

### Post by J-Rod on 2007-12-01
I am compiling xmame on Gutsy, it looks like I managed to get all the way through, and yet I am getting an error at the end I cannot figure out. Anyone who can help translate this for me, I would greatly appreciate it.

```
Linking xmame.x11 ...
/usr/bin/ld: cannot find -lugci
collect2: ld returned 1 exit status
make: *** [xmame.x11] Error 1

```

---

### Post by disturbedite on 2007-12-01
here is the solution:  don't compile xmame, its super out-dated.  its dead and has been since version 0.106 and mame is at version 0.121 right now.

use sdlmame.  its just a mame sdl port.  so if you want a frontend/gui, download [kxmame]("http://sourceforge.net/project/showfiles.php?group_id=145736&package_id=174814&release_id=514402") (<-- this build specifically, do not install any other build or the package available in the ubuntu repo, its outdated and does not support sdlmame).  you have to compile that kxmame package tho.  if you can't get it to compile, do this instead:
```
./configure --disable-joystick
```
that should let it compile, but of course the catch is that you won't be able to use a joystick or pad.

---

