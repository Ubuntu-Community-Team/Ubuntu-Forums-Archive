---
title: "Desktop background"
date: 2010-02-06
forum: Desktop Environments
---

### Post by TXbirder on 2010-02-06
I plan to use my own photos as desktop backgrounds.   And, when I'm not actively working, I'd like to see just the picture without a screen full of icons obscuring it.

I've found out how to move the panel with "favorites", "files and folders", etc off-screen until I select something.  How do I make all these icons go away until I select  "Favorites", or "Graphics", or another?"    Also, how to make them go away when I'm finished but not ready to turn off the computer yet.

Right now the desktop is still using the default settings for Netbook Remix, effectively obscuring my nice photo.

John

---

### Post by weblordpepe on 2010-02-06
Hello there. 

Would a screensaver full of pictures do? I'm sure theres a screensaver which lets you choose a folder full of photos to scroll through.

Theres also some other options about for disabling that netbook remix menu, and some options for turning off desktop icons.

Whats the effect you're after exactly? Do you want the icons/menu etc to dissapear until you wiggle the mouse or start using the computer or something like that?  I'm sure we can come up with something.

---

### Post by TXbirder on 2010-02-06
Well,  I like the way I have my WinXP desktop set up-  no shortcut icon.  Just quick-start icons in the task bar at the bottom.  I have a less-used icons in a folder titled  Seldom Used Icons. The rest of the screen(about 95%) is just a nice picture.

I'd like something like that- the panel on the left side as far left as possible, the tiny tool bar at the top, nothing else on the screen except my nice picture until I select Files and Folders or some other.

This may not be possible with the reduced capability of Netbook Remix.


John

---

### Post by weblordpepe on 2010-02-13
Hi dude. Never say impossible with linux :D

Its actually a seperate program thats drawing that flabby menu and stuff in netbook remix. Its called **netbook-launcher**.

Its rigged as part of the 'startup programs' for the desktop. Its along side things like the wifi connections manager and all that stuff.

I dont know how to find it from the menu and stuff, but if you can get yourself to a terminal, run this:
```
gnome-session-properties
```
This will bring up the list of programs rigged to start up as part of your desktop session. Scroll down to 'Netbook Launcher' and untick it. That should be all there is to it. It should dissapear. Or at the very least not be there when you login next.

:)

---

