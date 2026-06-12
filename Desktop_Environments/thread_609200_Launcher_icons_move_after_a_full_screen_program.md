---
title: "Launcher icons move after a full screen program"
date: 2007-11-10
forum: Desktop Environments
---

### Post by rohan000 on 2007-11-10
If you put any application launchers into the top panel and then run a full screen program, they all get moved around (usually all get pushed to the right side), even if they are locked. I had this problem in Feisty and the same thing happens in gutsy. Any full screen games seem to do it, as well as wine or dosbox in full screen.
Is there some way to save the panel item configuration so that I can easily reload it instead of manually moving the icons around after every time I run a full screen game?

---

### Post by atomkarinca on 2007-11-10
the thing causing this is: when you run a game, most probably the screen resolution changes to a lower one. that makes the icons to get arranged according to that resolution. the solution i could think of is that you can run the games in a virtual desktop. open "configure wine", under the graphics tab, you will see an option called "emulate a virtual desktop", check that box and enter the game's resolution then click ok. that's about it.

---

### Post by rohan000 on 2007-11-10
thanks, can you do something like this for regular linux programs too?

---

