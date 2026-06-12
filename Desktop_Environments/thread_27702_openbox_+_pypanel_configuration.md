---
title: "openbox + pypanel configuration"
date: 2005-04-17
forum: Desktop Environments
---

### Post by tread on 2005-04-17
So I got pypanel installed and I'm trying to run openbox + pypanel .. 

Pypanel looks nice, transparent .. but the system tray area isn't .. the gaim icon or any other system tray icon sticks out like a sore thumb. I want to use docker to hold the system tray icons, and stick pypanel to the top of the screen. I tried disabling the tray in the pypanelrc file in my home directory .. but that didn't work. (I did that by setting tray=0 in the panel configuration part of the file.) I haven't tried to move pypanel to the top yet though.

Also, is there some nice script to get the gnome-menu in openbox format?

Any suggestions? 
Thanks in advance!

---

### Post by tread on 2005-04-17
Ouch! (OK, I goofed up .. pypanel is now up with the tray disabled, and at the top of the screen.)

However, I still have a problem, this is the order I do things:
1. start pypanel
2. start docker
3. start gaim

pypanel crashes!

[I]sampanna@genua:~ $ Traceback (most recent call last):
  File "/usr/bin/pypanel", line 795, in ?
    PyPanel(display.Display())
  File "/usr/bin/pypanel", line 98, in __init__
    self.loop(self.display, self.root, self.window, self.panel)
  File "/usr/bin/pypanel", line 654, in loop
    if e.window.id in panel[section].tasks:
KeyError: 0

[3]-  Exit 1                  pypanel

[/I]

If I start pypanel again, then it seems to work fine.
What am I doing wrong? Also, the openbox menu question is still there.

Edited to add: pypanel seems to crash when I close the last window on the current desktop too! I've gone back to using gnome-panel for the moment : ](*,) 

perlpanel .. I again have issues with that. I can't move it to the top of the screen or change the width ,  though the config tool says I should be able to do that. Some of the applets don't work either.

---

### Post by ginobvhc on 2008-03-21
if your running docker . .. y get the icons of openbox..
your must kill docker and restar pypanel...

about the error of pypanal your have to reintall python 
becose there are a error to find olne module of python maybe errase

sorry my bad english

---

### Post by canistra on 2008-03-21
Try replacin docker with trayer ( nice alternative )

---

### Post by urukrama on 2008-03-24
Fbpanel is nice as well. If you like pypanel's aesthetics and only need a task list, you could try tint task manager.

---

