---
title: "What to do if xterm hangs?"
date: 2006-07-02
forum: Desktop Environments
---

### Post by shamael on 2006-07-02
Ok, so it sometime happens that a program freezes and that both xterm and the gnome system monitor become inaccessible (can't kill the misbeahaving process :evil:)...
I tried killing the X session with CTRL+ALT+BACKSPACE and logging in again but even with the failsafe gnome all I get is an empty desktop and a cursor.
The other day I tried logging in with the terminal instead and I've found that the processes that weren't responding were still there, so I just typed kill -9 -1 and I finally managed to restart a proper gnome session. So is that how it is supposed to be? I have been using linux for only a few months so I would like an advice on how to handle those situations.

Thanks!!!

---

### Post by angkor on 2006-07-02
If your keyboard still responds you could try: Ctrl+Alt+F1 and log in at the console. Usually you can then kill the program with:

```
killall {program-name}
```

If you don't know the exact name you can try searching for it:

```
ps aux | grep {program-name}
```

To get back to gnome: Ctrl+Alt+F7

---

### Post by shamael on 2006-07-02
Cool! I'll try it next time it happens :D

---

