---
title: "Compiz"
date: 2009-02-11
forum: General Help
---

### Post by RedSingularity on 2009-02-11
I have noticed that when i set Metacity into terminal "metacity --replace" it does switch.  However i cannot switch it back to Compiz without restarting X.org (ctr+alt+backspc).  Is there a way to get back to compiz without restarting?

---

### Post by geirha on 2009-02-11
Have you tried "compiz --replace &" ? If it doesn't work, what is the output you get?

---

### Post by RedSingularity on 2009-02-11
I cant even type in the terminal once i type Metacity --replace.  I cant do anything except move the mouse.  All the bars on the tops of the windows disappear to so i cant minimize or close anything.  This all happens once i close the terminal that i used for Metacity --replace.

---

### Post by geirha on 2009-02-11
Ah, yes. That is because when you close the terminal, it closes metacity along with it, since it is a child process of the terminal.

If you instead run 
```
metacity --replace &
```
To send metacity to the background, then type exit, it should work just fine. Or do it all in one line:
```
metacity --replace & exit
```

An even better option though, is to just hit Alt+F2 to get the run dialog and type in "metacity --replace" or "compiz --replace" there.

EDIT: Oh and a third option is to install [fusion-icon](apt:fusion-icon). Once installed, start it from Applications -> System Tools -> Compiz Fusion Icon. It will put itself in the notification area on your panel, and you can right-click it to switch between compiz and metacity.

---

### Post by RedSingularity on 2009-02-11
PERFECT!  Thanks a bunch!!!

---

