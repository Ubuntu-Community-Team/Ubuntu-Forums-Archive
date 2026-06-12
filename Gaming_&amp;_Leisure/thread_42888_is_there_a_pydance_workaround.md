---
title: "is there a pydance workaround?"
date: 2005-06-19
forum: Gaming &amp; Leisure
---

### Post by kiwibird on 2005-06-19
I haven't gotten pydance to work, after selecting song and all and expecting the actual playing of the game to start, it exits with this output:
```
Searching for courses in ~/.pydance/courses
Searching for courses in /usr/local/share/games/pydance/courses
Traceback (most recent call last):
  File "/usr/games/pydance", line 205, in ?
    if __name__ == '__main__': main()
  File "/usr/games/pydance", line 195, in main
    menudriver.do(screen, (songs, crs, screen))
  File "/usr/share/games/pydance/pydance.zip/menudriver.py", line 262, in do
  File "/usr/share/games/pydance/pydance.zip/menus.py", line 184, in display
  File "/usr/share/games/pydance/pydance.zip/menus.py", line 57, in activate
  File "/usr/share/games/pydance/pydance.zip/menudriver.py", line 155, in wrap_ctr
  File "/usr/share/games/pydance/pydance.zip/gameselect.py", line 205, in __init__
  File "/usr/share/games/pydance/pydance.zip/gameselect.py", line 227, in loop
  File "/usr/share/games/pydance/pydance.zip/songselect.py", line 232, in __init__
  File "/usr/share/games/pydance/pydance.zip/songselect.py", line 325, in loop
  File "/usr/share/games/pydance/pydance.zip/dance.py", line 192, in play
  File "/usr/share/games/pydance/pydance.zip/player.py", line 227, in __init__
AttributeError: 'module' object has no attribute 'Stats'

```

There's a bug report on it here:
[https://launchpad.ubuntu.com/malone/tasks/313/+edit ](https://launchpad.ubuntu.com/malone/tasks/313/+edit ), but I was wondering if anyone knows of a workaround?

---

### Post by miscz on 2005-06-20
There's always Stepmania, quite resource hungry but much more feature rich. 3.9-rc3 is pretty stable and I haven't got any problems with it.

---

