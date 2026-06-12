---
title: "Crashing Fullscreen game is unexitable!!"
date: 2009-01-09
forum: General Help
---

### Post by brnetonboy on 2009-01-09
I installed Lincity NG and it worked for about 3 seconds and then the display went crazy. I can kind of tell that the game is still there--i can click on things and stuff happens, but you can't read what it says or really see anything.

So I can't find the navigation to EXIT the game! And it's fullscreen, so I can't close it! I can't even use the "kill misbehaving app" button on my taskbar! There must be a linux alternative to ctrl-alt-del to pull up a list of apps and kill the one that is blocking everything else. Or exit fullscreen somehow. No function keys work, I pounded randomly on the keyboard for 10 minutes. 

Please help! Thanks.

---

### Post by binbash on 2009-01-09
I am opening drop down terminal for that kind of issues(and kill the pid).Worst case there is ctrl + alt + backspace

---

### Post by thedarkwinter on 2009-01-09
Hi

I think you can set up a shortcut to bring up Gnome System Monitor but i'm not sure how. It sounds in this case as thought the graphics options might be set wrong in the game.

run
```
lincity-ng --window

```

to start in windowed mode, and then try changing the graphics options.

when in full screen mode, just pushing escape should quit the game though.

cheers,
michael

---

### Post by uwes on 2009-01-09
You can use Ctrl+Alt+F2 (or F1, F3, etc.) to get a command line login. There, you can use kill to exit the program you want (or use htop if you don't know process name or number)

---

