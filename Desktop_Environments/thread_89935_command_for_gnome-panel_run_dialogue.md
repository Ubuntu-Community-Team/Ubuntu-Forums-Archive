---
title: "command for gnome-panel run dialogue"
date: 2005-11-13
forum: Desktop Environments
---

### Post by manicka on 2005-11-13
Does anyoone know the command to bring up the gnome-panel run dialogue? 
I'm trying to make a keybinding in the xfwm4 window manager. So far I've tried 

gnome-panel-control --run-dialog

without success

---

### Post by 23meg on 2005-11-13
Perhaps you need to have gnome-panel running? Do you?

---

### Post by manicka on 2005-11-13
Yes, I'm in gnome running xfwm4 instead of metacity with the usual two panels

---

### Post by 23meg on 2005-11-13
gnome-panel-control seems to be an openbox command, maybe it has something to do with that?

---

### Post by manicka on 2005-11-13
ok,

when you hit alt-f2 with metacity as the window manager, there must be some command that is passed to bring up the gnome run dialogue. That's what I'm after.

---

### Post by Dr. Nick on 2005-11-13
The gnome-panel-control --run-dialog command works fine for me using metacity. it maybe a metacity only feature and not necessarily a seperate application that can be launched seperate

EDIT
I ran the command openbox --replace and your command still worked, though alt+f2 didnt since metacity wasnt running

---

