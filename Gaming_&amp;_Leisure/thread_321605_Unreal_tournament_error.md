---
title: "Unreal tournament error"
date: 2006-12-19
forum: Gaming &amp; Leisure
---

### Post by christooss on 2006-12-19
I installed UT with loki installer and when I try to run ut there is this error
```

$ ut
/usr/local/bin/ut: 29: Syntax error: Bad substitution
```

This is first Unreal Tournament

---

### Post by Hemmer on 2006-12-19
did you run the installer as root? for some installers this is nescessary and will mess up if you dont. Try reinstalling as root:

```
sudo ./unrealinstaller.sh
```

---

### Post by christooss on 2006-12-19
I did run it as a root

I can run ut with running ut-bin in ut/System directory but not with linked files

---

### Post by argie on 2006-12-22
If you run it from the console, try this:

```
gedit ~/.bashrc
```

and add these two lines to it:

```
# UT Data Path
export UT_DATA_PATH=/usr/local/games/ut/System
```
That last path is the path to ut-bin. It may be different. I just had it as default in the Loki installer.

There seems to be another solution here though:
[http://www.linuxquestions.org/questions//showthread.php?p=1216070#post1216070](http://www.linuxquestions.org/questions//showthread.php?p=1216070#post1216070)

---

