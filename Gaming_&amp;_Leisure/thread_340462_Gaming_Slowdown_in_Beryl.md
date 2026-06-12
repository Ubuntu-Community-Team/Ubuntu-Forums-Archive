---
title: "Gaming Slowdown in Beryl"
date: 2007-01-17
forum: Gaming &amp; Leisure
---

### Post by Eddie Wilson on 2007-01-17
Good Day All,
I've installed Beryl and now some of my games, (the ones I run under crossover linux) are very slow. These are the Hoyle card and board games. Has anybody else had this problem? My other games seem to play fine tho some of the game menus cannot be read. Anyway just a little question. No big problem.
Have a Good One,
Eddie

---

### Post by murlosad on 2007-01-17
If you haven't already, you might try switching back to metacity or kwin whichever you use when you want to play a game.

I'm not familiar with the Hoyle games, but if they need any 3d acceleration they probably won't work to well in Beryl.

I usually write a script to launch my games so that if, for instance, I need to kill Beryl first I can do it easily, e.g:

```
#!/bin/bash

kill beryl &&
"insert game command here" &&
beryl &&
```

which will kill beryl and then restart it when I'm finished with the game.  Probably only want to use something like this for full screen games though.  If you are running in windowed mode, I think I would try just switching between beryl and the default window manager.

I think there might also be an option in the Window Attribs settings to set the rendering for individual applications. Not sure on that one, someone else will probably know.

---

### Post by Eddie Wilson on 2007-01-17
Thanks. I've been switching window managers in order to play these games without any problems. The script writing ideal would be good for my wife. She likes to play her Hoyle games and also she likes Beryl. I can switch back and fourth easily but she can't. I might have to teach her how to do that. Again thank you for your help.
Eddie

---

### Post by hikaricore on 2007-01-17
Hi, why don't you just use beryl-manager so you have a tray icon to change your current window manager?  I don't see the use of a script when there is already an application made by the beryl team for this specific function.

---

### Post by murlosad on 2007-01-17
True, you could use beryl manager to do the switching, but the idea behind the script (and I should note, I can't take credit for it, I pulled it from one of the warcraft threads), is so you can setup a launcher icon, and have it do everything in one click. It just kinda streamlines the process that's all, but it essentially does the same thing.

---

