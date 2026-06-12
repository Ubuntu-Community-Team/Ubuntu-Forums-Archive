---
title: "Window Size/Position"
date: 2006-09-22
forum: Desktop Environments
---

### Post by SonWon on 2006-09-22
Is there a command that will tell me the size and position of a window?

I tried xprop but did not see the information listed?

Also, how do I view the man pages for --geometry?  I tried man X but that did not work?

Oh, and is there a similar command (--geometry) that will send a window to a different workspace?

Thank you,

---

### Post by croak77 on 2006-09-22
xwininfo

---

### Post by ayoli on 2006-09-22
geometry option usually works like that:
[COLOR="Green"]width[/COLOR]x[COLOR="Green"]height[/COLOR]+[COLOR="Green"]horizontal_pos[/COLOR]+[COLOR="Green"]vertical_position[/COLOR]
with an example:
```
gnome-terminal --geometry 480x320+220+180
```

---

### Post by skymt on 2006-09-22
You can use [Devil's Pie](http://www.burtonini.com/blog/computers/devilspie) to customize what workspace windows appear on (and just about everything else about a window).

---

### Post by SonWon on 2006-09-23
Thank you very much for the replies.  I got it working using the --geometry setting and xwininfo gave me the current size.  I adjust the window to how I like and then set the geometry settings.  Note, character based windows use character sizes not points on the screen for the window size that threw me off for a few mnutes.

Devil's Pie is a very powerful app but it needs one more feature to make it really useful.  I want to be able to right click or select from a menu a command like save window position, save window size, etc..  This would make Devil's Pie useful to the newbie to use.

Thanks again to everyone.

---

