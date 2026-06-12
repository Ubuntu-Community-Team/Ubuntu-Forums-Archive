---
title: "What to do when games freezes"
date: 2009-03-19
forum: General Help
---

### Post by s001s on 2009-03-19
Installed Quake4 and my character randomly gets stuck and can't move... The whole game kinda freezes as I can't press esc to quit the game all you can do is to look around until you press the reset button.

My question is since you can't press ctr+alt+del to bring up system monitor or any process killing app to end a non responsive game in full screen mode what do you do? I've tried everything from the above to alt+tab, Alt+F2 and xkill. Its easy to end a program when you are on the desktop but not when running full sreen games...:(:(:(

---

### Post by lostandcold on 2009-03-19
I also have this problem due to my computer being rather powerless when it was brought 5 years ago let alone now.  Still yet to find a decent fix, although I found alt + F9 works for a few games but not for others.

---

### Post by khelben1979 on 2009-03-19
```
ctrl + alt + backspace
```
should be able to kill the x-server

```
ctrl + alt + f1
```
takes you to the first text console. From there you can login and look up processes with the top command and then use ```
sudo kill -9 [process number]
```

---

### Post by s001s on 2009-03-19
so there is no way to minimise games to the desktop...

---

### Post by khelben1979 on 2009-03-19
I think that you really need to change the graphics settings inside the game to be run in window mode and then when it crashes, either the whole x-server freezes or just the window. In the latter case you can use xkill to terminate the process.

I saw that there were a Quake 3 minimizer for Windows when I googled around a little. There "might" be one like this for the Linux version of Quake 4 somewhere, but I was unable to find one.

---

### Post by fieroboom on 2009-03-19
Whenever I experience a lockup like that, I always break out my laptop, SSH to the frozen machine, and kill the culprit process, kill X, or whatever needs to be done. I had to do it several times when I was experimenting with multiple X sessions.
So if you have a second computer, that's definitely the way to go, but if not, did you try CTRL+ALT+Right Arrow ? In your window manager, that should switch desktops (workspaces) to the one on the right, which shouldn't have anything open on it, and maybe you could go from there. However, if the key bindings for CTRL+F1 and CTRL+ALT+BACKSPACE aren't working, then that probably won't work either...
:D
-Paul

---

### Post by ruel- on 2009-03-19
I usually just Ctrl+Alt+Backspace, then relogin again. In taht case, I make sure that I close important apps before playing any games..

---

