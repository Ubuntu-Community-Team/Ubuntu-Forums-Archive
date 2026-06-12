---
title: "initial window size"
date: 2008-09-04
forum: Desktop Environments
---

### Post by savvdm on 2008-09-04
Every time I open Gnome Terminal, its window always appears in the middle of the current desktop, approximately half the width and heights of it. How can I change this default size and position?

---

### Post by rye_ on 2008-09-04
i've never done this myself, but perhaps by looking at the options in gconf-editor may help.

run in the terminal;

gconf-editor

---

### Post by savvdm on 2008-09-05
Thanks for the suggestion!
I tried to add '--geometry 100x40' to gnome-terminal command line via gconf-editor, but that did not work for some reason.
However, I found another way to fix this. I previously made a toolbar button to quickly start the terminal. (The button was made by dragging the corresponding menu item to the toolbar). Now I right-clicked that button, and chose Properties. There I added --geometry 100x40 to the command line. Now the terminal window opens large enough to work with. I still don't know how to change the window's position on the screen, but that's not a big issue.

---

### Post by jotego on 2009-11-06
You can change both size and position using a command like this one:

gnome-terminal --geometry=100x31+0+580

It also works with other X applications although some times you have to use -geometry (one hyphen) instead

---

