---
title: "How to change the default GNOME window manager."
date: 2009-05-06
forum: General Help
---

### Post by dragos240 on 2009-05-06
How can I do this? I saw this before.

---

### Post by monsterstack on 2009-05-06
Log out, then choose the sessions option from the menu and select the window manager of your choice and log back in. You'll be asked if you want to make it the default via a prompt.

---

### Post by dragos240 on 2009-05-06
Yes, but I mean INSIDE gnome, metacity is the default one.

---

### Post by monsterstack on 2009-05-06
Well, typing

```
killall metacity && yourwindowmanager
```

into the terminal will do the trick. To make it permanent, go to the gconf-editor

```
gconf-editor
```

and navigate to desktop>gnome>applications>window manager, then change the value for "default" to the path to your preferred manager.

---

### Post by Sealbhach on 2009-05-06
I use the Compiz Fusion Icon. I switch to Openbox if I want to start up a game. 

.

---

