---
title: "bash script for gamma brightness"
date: 2010-07-31
forum: Gaming &amp; Leisure
---

### Post by themanfromearth on 2010-07-31
hi forum, im new at this things, i installed linux 3-4 days ago and im not really familliar with some stuff, i was windows user since 2000.
I had some problems playin game(Heroes of newerth), if the compiz is turned on, i had huge bugs, like lag and bad graphics.
I installed latest nvidia drivers for my 8800GT(256.35 driver), compiz is working fine, but as i said, hon isnt.
I turned off compiz and game is runing almost as on windows(same effects in game are still not the same as on win7).Then i tryed elimination some compiz components to see whats causiing the problems, and it was cube plugin, i disabled all 3d stuff in compiz, left animation, wobbly windows, and some other minor stuff, turned on. Game is runing fine, but now the problem is that i cant change brightness in game, its to dark on default, slider doesnt do anything.

xgamma -gamma 1.3 .... runing that in terminal does the job, now i ask u more experienced linux users, if u can help me to do that automaticly, every time i start game, and after game is closed, to revert gamma to 1.0

help :o

---

### Post by DoktorSeven on 2010-07-31
```

#!/bin/bash
xgamma -gamma 1.3
gameexecutablenamehere
xgamma -gamma 1.0

```
Save to file, set Executable in file permissions (or chmod +x yourfilename), and run it (or make a shortcut to it on your desktop or wherever).

---

### Post by themanfromearth on 2010-08-01
> **DoktorSeven said:**
> ```

#!/bin/bash
xgamma -gamma 1.3
gameexecutablenamehere
xgamma -gamma 1.0

```Save to file, set Executable in file permissions (or chmod +x yourfilename), and run it (or make a shortcut to it on your desktop or wherever).

nothing hapenned, just one screen flickr and its same gamma again....

---

### Post by DoktorSeven on 2010-08-01
Make sure you're putting the right game command in there where I have "gameexecutablenamehere".  Depending on what and where it is you might have to add a **cd** command to get to the right directory, e.g. if you have a game called "Foo" and its executable is called **foo** in the directory "/home/myuser/foo-1.0", you'd do:

```

#!/bin/bash
xgamma -gamma 1.3
cd /home/myuser/foo-1.0
./foo
xgamma -gamma 1.0

```

Otherwise, if the game executable is in your PATH (/usr/bin, /usr/local/bin, /usr/games), just typing the name of the executable is good enough, no **cd** command or ./ preceding it necessary.

---

### Post by themanfromearth on 2010-08-01
> **DoktorSeven said:**
> Make sure you're putting the right game command in there where I have "gameexecutablenamehere".  Depending on what and where it is you might have to add a **cd** command to get to the right directory, e.g. if you have a game called "Foo" and its executable is called **foo** in the directory "/home/myuser/foo-1.0", you'd do:

```

#!/bin/bash
xgamma -gamma 1.3
cd /home/myuser/foo-1.0
./foo
xgamma -gamma 1.0

```

Otherwise, if the game executable is in your PATH (/usr/bin, /usr/local/bin, /usr/games), just typing the name of the executable is good enough, no **cd** command or ./ preceding it necessary.

ITS WORKING ! :p thx ! :popcorn:

---

### Post by Allwynd on 2011-10-15
im sorry im reviving an old thread, but i have done this:

1. i created a blank file
2. added 
```
#! /bin/bash
xgamma -gamma 1.5
``` into it
3. made it a startup item

but still, after restart it wont work, im using ubuntu 11.10
somewhere i read that it requires X to be running, but im not a techy guy, i dont really understand
ubuntu 11 has unity, does this mean the X thing is not working?

or ... can you just give a simple screen calibration program, that saves the settings, like ATI Catalyst on Windows

because i have this ****** old monitor, which is probably made in the year 2000 and its really dark, even when brightness and contrast are set to 100

so this is my problem, i dont really play games or care about them


thanks in advance, i hope someone helps me out here

---

