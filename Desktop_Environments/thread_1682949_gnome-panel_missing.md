---
title: "gnome-panel missing"
date: 2011-02-06
forum: Desktop Environments
---

### Post by wwbdd on 2011-02-06
My gnome panel seems to have gone missing.  I found on several sources online that if worse comes to worse, then you can just delete everything and start anew, but even after doing that, my gnome panel is missing.  I tried:

```
rm -rf .gconf* .gnome*
```

from a remote ssh session (so not while I was in a gnome session).  Then I logged into gnome, and my panel is still missing.  I can start it by opening up a terminal and running:

```
gnome-panel
```

but I'd like for it to start up normally.  Is there a way I can reset my entire gnome environment to be just as it was when I installed everything?

---

### Post by Krytarik on 2011-02-06
> **wwbdd said:**
> but I'd like for it to start up normally.  Is there a way I can reset my entire gnome environment to be just as it was when I installed everything?
You would have done it with the first mentioned commands (OMG, is this harsh! LOL), if executed properly.

However, do this (while logged in normally):
- enter "gconf-editor" in a terminal
- browse to "/desktop/gnome/session/required_components/panel"
- set it to "gnome-panel"

---

### Post by wwbdd on 2011-02-06
Unfortunately, that didn't work either.  I got things working in a rather hackish way by adding a startup application for gnome-panel.  I'm still open to suggestions on how to get things working properly though, if for no other reason than sheer curiosity.

---

### Post by Krytarik on 2011-02-06
What is the entry for this then, in gconf-editor?: /desktop/gnome/session/required_components_list .

The default is a list with entries of the type "string" with "windowmanager", "panel" and "filemanager" in it.

---

### Post by wwbdd on 2011-02-09
filemanager = nautilus
panel = gnome-panel
windowmanager = gnome-wm

This is rather baffling.

---

### Post by Krytarik on 2011-02-09
> **wwbdd said:**
> filemanager = nautilus
panel = gnome-panel
windowmanager = gnome-wm

This is rather baffling.
Yeah, but did you also check this?:
> **Krytarik said:**
> /desktop/gnome/session/required_components_list .

The default is a list with entries of the type "string" with "windowmanager", "panel" and "filemanager" in it.

---

### Post by wwbdd on 2011-02-09
Yea, that's alright too.  I guess I'll just have to stick with calling gnome-panel with an autostart script.  Thanks for your help.

---

### Post by Krytarik on 2011-02-09
> **wwbdd said:**
> Yea, that's alright too.  I guess I'll just have to stick with calling gnome-panel with an autostart script.  Thanks for your help.
Ok then. Calling it with an startup launcher isn't really different from the "normal" way.

---

