---
title: "Randomly exiting full screen"
date: 2008-08-10
forum: Gaming &amp; Leisure
---

### Post by RevolutionMaster on 2008-08-10
When playing a game in full screen (Scorched3D, Tremulous, all other quake engine games) it will randomly leave full screen, and it will refuse to accept any input until it returns to fullscreen in about 1 minute. 
Thanks in advance for the help.

---

### Post by Perfect Storm on 2008-08-11
It's because of Compiz. Disable it first.

You can do it via Fusion-Icon or making a script launcher for a game which automatically disable compiz, then launch the game, after exiting the game it will enable compiz.

Example:
```
#!/bin/bash 

metacity --replace & 

cd ~/.Games/OpenTyrian 
./tyrian 

compiz --replace & 



```

---

### Post by ramenite on 2008-08-11
There's also an option under the Compiz settings called "Unredirect Fullscreen Windows". If you want things to go full screen with Compiz, you need to turn this off.

---

