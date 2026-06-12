---
title: "panels not showing in Ubuntu Hardy Heron"
date: 2008-06-17
forum: Desktop Environments
---

### Post by scottybowl on 2008-06-17
I recently restarted my computer and all the panels have disappeared. I am able to open the folders on my desktop and as a result can browse to the terminal. I have followed a number of topics saying to delete the .gnome folders, refresh metacity etc.

When I press ALT-F1 I just see a blank screen. I have tried logging out/in and restarting numerous times.

One thing I did before restarting was to completely remove Evolution via the Synaptic interface. Could this have caused the problems?

Any ideas on how to fix this would be greatly appreciated.

---

### Post by damis648 on 2008-06-17
In terminal:
```
gconftool-2 --shutdown

rm -rf ~/.gconf/apps/panel

pkill gnome-panel
```

EDIT: to open a terminal - press alt+f2 and type
```
gnome-terminal
``` and enter.

---

### Post by scottybowl on 2008-06-17
Thanks for the quick reply!

I tried pressing ALT-F2 and it doesnt do anything. I also tried the commands and once again nothing happens :confused:

---

### Post by scottybowl on 2008-06-17
Ok, I discovered the problem!

For some reason gnome-panel was not installed. I ran:

sudo apt-get install gnome-panel

then

gnome-panel 

And it started the panels up!

---

### Post by damis648 on 2008-06-17
Ah, thats good.

---

