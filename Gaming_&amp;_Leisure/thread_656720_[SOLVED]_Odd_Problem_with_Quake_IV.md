---
title: "[SOLVED] Odd Problem with Quake IV"
date: 2008-01-02
forum: Gaming &amp; Leisure
---

### Post by evil_urna on 2008-01-02
After struggling with the installer for a while I got quake IV to run beautifully. But I ran into a strange problem

Randomly, it seems, the game will pop into window mode. It does not crash, lock up, or even studder. But I lose control of the game. It is still running fine but it will not respond to any mouse or keyboard commands. The only thing I am able to do is ctrl-alt-backspace. Please help

---

### Post by Cappy on 2008-01-03
You can turn the screensaver off or use
```
killall gnome-screensaver
```
before you launch the game. If you edit your menu I think you can add it on the front to look like this:
```
killall gnome-screensaver; quake4
```

Replace "quake4" with whatever the command is that is used to launch quake4

---

### Post by evil_urna on 2008-01-03
> **Cappy said:**
> You can turn the screensaver off or use
```
killall gnome-screensaver
```
before you launch the game. If you edit your menu I think you can add it on the front to look like this:
```
killall gnome-screensaver; quake4
```

Replace "quake4" with whatever the command is that is used to launch quake4


Good lord how could it be so simple.

I love you

---

### Post by zwastik on 2008-03-16
make a bash script named quake4.sh

```
#!/bin/bash

killall gnome-screensaver && quake4 && gnome-screensaver
```


So it will kill gnome-screensaver before running Q4 and load it after you quit Q4.

---

### Post by eragon100 on 2008-03-16
Start with disabling compiz if it's activated, that often causes problems with games.

---

### Post by Fadetoz on 2009-07-17
No freaking kidding.. I thought this was a Jaunty bug and never had a problem with this happening until I upgraded. No wonder it happens after 10 min of playing the game. This was really pissing me off. [COLOR="Blue"]THANKS FOR THIS POST[/COLOR] as I just loaded up Jaunty 64 on what was my Windows XP hard drive.

Sometimes the fix is so simple you would never think of it..lol

---

