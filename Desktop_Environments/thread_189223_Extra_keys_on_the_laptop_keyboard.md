---
title: "Extra keys on the laptop keyboard"
date: 2006-06-04
forum: Desktop Environments
---

### Post by Slace on 2006-06-04
I've got an Acer TravelMate 650 and as with most laptops it has some extra buttons and commands that can be issued from the function key.

What can I use to map the keys? I've checked xev and it registers the key events, just not sure how to catch the events and do something with the,

---

### Post by Wermut on 2006-06-05
If you have got the keycodes, you can create a file (e.g. ~/.Xmodmap) and add some lines like the following to it (these are the lines for my laptop):

keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 160 = XF86AudioMute

You said that you know the keycodes; however I don't know what the names of the commands you need are.

Then make sure that the command xmodmap ~/.Xmodmap is executed everytime at startup (for example, by placing it into a file in /etc/X11/Xsession.d or ~/.kde/autostart

---

### Post by NESFreak on 2006-06-05
try
system-->preferences-->hotkeys

---

### Post by adamkat on 2006-06-08
which file in /etc/X11/Xsession.d ?
I run xubuntu if it makes any difference.
thanks

---

### Post by Wermut on 2006-06-12
The files are executed in alphabetical order (thus the numbering); I use a file called 95autostart.

---

