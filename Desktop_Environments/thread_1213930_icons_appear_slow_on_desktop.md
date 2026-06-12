---
title: "icons appear slow on desktop"
date: 2009-07-15
forum: Desktop Environments
---

### Post by gabello on 2009-07-15
Hi,
I'm new at using xfce 4 and one of the issues I encountered is the following: Every time I click "show desktop" icon the icons from my desktop (3 or 4, not more) appear only after 2,3 seconds of waiting, although the desktop (background image) is shown instantly. During this interval the cpu is not loaded to high values and this behaviour replicates every time no matter how many windows I have opened. Any idea on this?
Thanks

---

### Post by gianluca.pettinello on 2009-07-15
Hi
open a terminal and:
cd /usr/share/icons
sudo fc-cache *

It should cache your icons

then

cd /usr/share
sudo fc-cache pixmaps

Hope you solved
Gianluca

---

### Post by gabello on 2009-07-16
Hi, Thanks for this, however it does not seem to work :(.
It's strange because I have xfce on a laptop with lower speqs. and lots of icons on desktop and they seem to "be there" all the time.
Another think, even if I go with one window above some icons from the desktop and then move it away from it it takes sometime until the covered icons appear.

---

### Post by bl1rt on 2009-07-17
I have the same problem. It seems to be an issue with the graphics driver (I have an old nvidia card). There is a solution described in the following article:

[http://techbase.kde.org/User:Lemma/KDE4-NVIDIA](http://techbase.kde.org/User:Lemma/KDE4-NVIDIA)

To sum it up: enter 

nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1

into a terminal (Obviously, this will only work if you have a nvidia card, but then again, you might not have the problem in that case).

It does remove the stuttering, but now the system freezes sometimes. Guess there are some xorg.conf options that will have to be explored.

As the InitialPixmapPlacement command will not be saved permanently, you will have to put the line into autostart or something for that.

Does that work for you too, gabello?

---

### Post by gabello on 2009-07-17
Yes, this works on my machine. Now I will see if there are any downsides of this change.

Thanks

---

