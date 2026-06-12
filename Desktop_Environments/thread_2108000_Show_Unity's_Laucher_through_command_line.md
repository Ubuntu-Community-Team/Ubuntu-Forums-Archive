---
title: "Show Unity's Laucher through command line"
date: 2013-01-23
forum: Desktop Environments
---

### Post by gco on 2013-01-23
**How can I show Ubuntu Unity's Launcher panel through terminal?**

I'm trying to bind a mouse button to this, showing the launcher. By "launcher" I mean the vertical panel with the "Home button". I would like to press this particular mouse button and it acts as if I had pressed the [FONT="Courier New"]<Super>[/FONT] key; which is bound to show the launcher by default.

I've set [FONT="Courier New"]xbindkeys[/FONT] properly already. I know I could use [FONT="Courier New"]xdotool[/FONT] (or [FONT="Courier New"]xte[/FONT]) to simulate a [FONT="Courier New"]<Super>[/FONT] keypress event, but I'm not willing to do that. I would rather use a more direct solution. Couldn't find any Unity's interface to do that though. Does anyone?

Thanks in advance.

---

### Post by stinkeye on 2013-01-23
You can't bind the super key directly.
You could use easystroke(mouse gestures) to bind the command
```
xdotool key Super
```
to a mouse button.

```
sudo apt-get install easystroke 
```
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10495426&postcount=11") for howto.

---

