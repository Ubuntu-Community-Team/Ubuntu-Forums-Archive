---
title: "Solution for alt+tab for HoN and some other games"
date: 2010-12-30
forum: Gaming &amp; Leisure
---

### Post by mariost on 2010-12-30
I've been searching for quite a long time how to make my HoN more tolerant towards switching workspaces, and in general, using anything else while it's running. And I came upon [this]("http://www.alientrap.org/forum/viewtopic.php?p=44930&sid=1d4c5622ff28cc91065f7f5a645deb76") thread, suggesting disabling in-game fullscreen and toggling windows manager's one on. So I started HoN (the game for which im doing all this fuss) and disabled fullscreen. Then used alt+F11 (default fullscreen toggle for WM) and its working the same as before. BUT! Now i can use alt+F11 again to toggle fullscreen off and switch workspaces, alt+tab and whatever ^^ So to automate the process, i created two files:

1min:
```

wmctrl -r :ACTIVE: -b remove,fullscreen
wmctrl -s 1

```1max:
```

wmctrl -s 0
wmctrl -r :ACTIVE: -b add,fullscreen

```**wmctrl** is just a program used to control the windows manager via commands, nothing scary.
I bound 1min to Super+g using the keyboard shortcuts menu, and 1max to Super+h.
So, the first button/script toggles windows manager fullscreen flag of the active program off (remember, from the game menu the fullscreen option must be turned off for good) and switches to workspace #2, 
while the second button/scripts switches back to workspace #1 and toggles fullscreen back on. You can change the line with "wmctrl -s <number>" to reflect the actual workspaces that you use while gaming, I am used to having first one for the game and the right one for other stuff. I can confirm it works flawlessly with Heroes of Newerth, got it working with Nexuiz only when I open console. Can't get it to work with Tremulous, but I suppose this method can be used with some other games too. It's a simple trick, though I spent several hours until I found this.  Hope someone else finds this useful, sharing it for the good of the linux community and my own sanity :)

---

