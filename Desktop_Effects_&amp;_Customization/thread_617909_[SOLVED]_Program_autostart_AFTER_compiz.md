---
title: "[SOLVED] Program autostart AFTER compiz"
date: 2007-11-19
forum: Desktop Effects &amp; Customization
---

### Post by MNICY on 2007-11-19
I need a program to autostart (which i know how to do), but not untill compiz-fusion is fully loaded.
Does not matter if it is in KDE or GNOME. (i will decide which desktop enviroment i will use depending on which one i can do this in).
I know how to autostart in KDE and in GNOME. I tried to do order in GNOME, but it is weird, and in KDE, i tried writing a script, but it did not really work. The script worked, but it went on to the next command before compiz was finished loading, ruining the point :'(
Help with this would be appriciated.

---

### Post by Romanus81 on 2007-11-19
if you add "sleep [time in seconds]" to your script before the program, it should make it wait.

sleep 10
[command]

---

### Post by MNICY on 2007-11-20
ok, thanks
it works (kind of. solved one problem, but there are still others)
```
#!/bin/bash
compiz --replace &
sleep 10 
gaim
```

---

