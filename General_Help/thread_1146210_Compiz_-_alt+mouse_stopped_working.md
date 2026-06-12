---
title: "Compiz - alt+mouse stopped working"
date: 2009-05-02
forum: General Help
---

### Post by spongemonkey on 2009-05-02
Hi guys,

I've searched through compiz checking for conflicting bindings and haven't found anything. I know its something to do with compiz because when I disable it I get the functionality back...

I used to be able to use alt + right mouse button to get a window's maximize/minimize/close etc menu to appear. The action is bound to this in compiz. Also I cant use alt + space to get the windows other menus to be selected, or alt + F1 for the main menu.

Any thoughts are appreciated, thanks.

---

### Post by spongemonkey on 2009-05-08
bump?

can't figure out whats wrong here...

---

### Post by cdude on 2009-05-08
Install compizconfig-settings-manager and change the key bindings the way you like.

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by spongemonkey on 2009-05-08
I have the settings manager installed, the actions are appropriately bound in it but I get nothing when I use the key/mouse combination

---

### Post by cdude on 2009-05-08
did you try reseting compiz settings? 

delete all .compiz/ .config/compiz/ .cache/compizconfig/ 

and restart compiz , see if it helps


note: if this is an upgraded system, I would delete all the old config files in the home folder.

---

