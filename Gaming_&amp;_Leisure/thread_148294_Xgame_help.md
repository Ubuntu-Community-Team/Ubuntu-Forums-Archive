---
title: "Xgame help"
date: 2006-03-21
forum: Gaming &amp; Leisure
---

### Post by junior aspirin on 2006-03-21
hi all. i have done some searching ie the following posts:
[http://www.ubuntuforums.org/showthread.php?t=51486&highlight=xgame](http://www.ubuntuforums.org/showthread.php?t=51486&highlight=xgame)
[http://ubuntuforums.org/showpost.php?p=781066&postcount=13](http://ubuntuforums.org/showpost.php?p=781066&postcount=13)

but i cannot seem to get xgame to work correctly.

on the first setup attempt when i launch doom3 from xgame i get the following:
*the screen blanks then goes grey with small stripes, and an X shape mouse curser appears.
*the screen the distorts this grey and does nothing.

*i have to ctrl alt backspace to getout of it

my second attempt at the config:
*screen blanks and loads grey stuff as above
*then the login screen appears, but with nautilus overlayed on it, but with no window manager running. i can use nautilus, even watch videos!

*then i have to ctrl alt backspace again


any ideas? i think i may have configured it wrong somewhere.

i use dapper with all the fancy xgl and compiz stuff, which is why i need to use xgame.

ati radeon 9800, amd athlon 64 3200+ on the k7 kernel.

i am hoping this is the best place to post.

---

### Post by KSDZ on 2006-03-30
I'm having exactely the same problem,
gray stripes and a non responding mouse,
however in my case ctrl+alt+backspace didn't help much either...

---

### Post by minisori on 2006-04-01
Do you want to run a game in another x?

Just do this for example for doom3:

```
sudo X :1 -ac & DISPLAY=:1 doom3
```

You can put it in a script if u want:

```
#!/bin/bash
sudo sleep1
sudo X :1 -ac & DISPLAY=:1 $1
```

Supossing u called dis script game, u run it as game doom3 or game anything_you_want_to_run_on_another_X

---

