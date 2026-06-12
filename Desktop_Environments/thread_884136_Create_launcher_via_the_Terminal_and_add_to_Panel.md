---
title: "Create launcher via the Terminal and add to Panel"
date: 2008-08-08
forum: Desktop Environments
---

### Post by syn4k on 2008-08-08
Is it possible to create launchers via the Terminal and or add them to the Panel via the Terminal?

---

### Post by cdtech on 2008-08-08
Sure is. You would just have to create the script.

---

### Post by syn4k on 2008-08-08
Yeah, I'm sure that I can code something but if I just do echo > ~/something.laucher that's not going to work. I need to know what the launcher must have in it and how I would write these entries into the Panel...

---

### Post by syn4k on 2008-08-08
Well...I guess I've done it again and asked a question nobody can answer :) haha

---

### Post by syn4k on 2008-08-27
Anybody else?

---

### Post by bazzer on 2008-10-01
At a wild stab in the dark, I'd say you'll be needing this spec:
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html]("http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html")
From what I see it's fairly straightforward to create a desktop launcher, but then adding to a panel is a whole can of worms. I've searched high and low and the best answer I can suggest at the moment is make the panel how you want it (that is, create all your launchers and such) then just export the panel file with
```
gconftool-2 --dump /apps/panel > panel_file
```
and then import it as part of a script
```
gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --load panel_file
```
hth

---

