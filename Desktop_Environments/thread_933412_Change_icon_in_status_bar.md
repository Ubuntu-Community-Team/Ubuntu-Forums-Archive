---
title: "Change icon in status bar?"
date: 2008-09-29
forum: Desktop Environments
---

### Post by Kinetic Being on 2008-09-29
How could I change the icon that a programs uses when it is active in the status bar (the place where the active program icons go next to the clock) in GNOME? I have Ubuntu Hardy, and I want to change the amarok icon, among others.

---

### Post by Sarai the Geek on 2009-03-26
I have this question too, so... *bump*

---

### Post by Kosimo on 2009-05-17
Me too!

---

### Post by Chiheb on 2009-05-17
[SIZE=2]hi all , here is my method who worked perfectly.
[U][COLOR=Red]
PS:don't try to change the default system icon[/COLOR][COLOR=Red] so try this with an other icon package [/COLOR][/U]

1-install Inkscape vector graphics editor with synaptic
2-now go to home/yourname/.icons (show hidden files with ctrl+h) and search the icon that you would replace,you can take a note for its path and name or simply let the window open :) (for exemple in my case the net status i can find it in home/your name/.icons/name of icon folder/scalable/app/22) 
3- open the new icon with Insckape(right-click open with) then click file--->export bitmap(shift+ctrl+E) 
4-a new window is open, let drawing checked, just change the size of the bitmap to fit your panel size
5-now click browse and naviguate to icon that you want replace(step2) click on it---->save----->replace.
6- type in terminal "killall gnome-panel" for changes to take effect.
[/SIZE][SIZE=2][COLOR=Red]important: the size of the new icon must be equal to the size of the old one[/COLOR]
[/SIZE]  [SIZE=2][COLOR=Red]and the most important they should have the same extension[/COLOR]
good luck [/SIZE][SIZE=2]and excuse my bad english :)[/SIZE]

---

### Post by Kosimo on 2009-05-17
> **Chiheb said:**
> [SIZE=2]hi all , here is my method who worked perfectly.
[U][COLOR=Red]
PS:don't try to change the default system icon[/COLOR][COLOR=Red] so try this with an other icon package [/COLOR][/U]

1-install Inkscape vector graphics editor with synaptic
2-now go to home/yourname/.icons (show hidden files with ctrl+h) and search the icon that you would replace,you can take a note for its path and name or simply let the window open :) (for exemple in my case the net status i can find it in home/your name/.icons/name of icon folder/scalable/app/22) 
3- open the new icon with Insckape(right-click open with) then click file--->export bitmap(shift+ctrl+E) 
4-a new window is open, let drawing checked, just change the size of the bitmap to fit your panel size
5-now click browse and naviguate to icon that you want replace(step2) click on it---->save----->replace.
6- type in terminal "killall gnome-panel" for changes to take effect.
[/SIZE][SIZE=2][COLOR=Red]important: the size of the new icon must be equal to the size of the old one[/COLOR]
[/SIZE]  [SIZE=2][COLOR=Red]and the most important they should have the same extension[/COLOR]
good luck [/SIZE][SIZE=2]and excuse my bad english :)[/SIZE]


Thanks for the guide!  I'm gonna follow it right now! ;)

---

