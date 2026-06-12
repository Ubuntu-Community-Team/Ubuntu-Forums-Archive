---
title: "QUICK QUESTION: How do I change my Gnome-Do docky position?"
date: 2009-09-20
forum: Desktop Environments
---

### Post by gymophett on 2009-09-20
I can't seem to find out how. I want it at the top of my screen. And it is nowhere in the preference option.

---

### Post by qamelian on 2009-09-20
You need to launch gconf-editor from Alt-F2. Navigate to ```
/apps/gnome-do/preferences/Docky/Utilities/DockPreferences
``` and locate the Orientation setting in the righthand pane. Change **bottom **to the value you prefer.

---

### Post by gymophett on 2009-09-20
> **qamelian said:**
> You need to launch gconf-editor from Alt-F2. Navigate to ```
/apps/gnome-do/preferences/Docky/Utilities/DockPreferences
``` and locate the Orientation setting in the righthand pane. Change **bottom **to the value you prefer.

It's amazing how I don't even have that folder. :O

---

### Post by qamelian on 2009-09-20
> **gymophett said:**
> It's amazing how I don't even have that folder. :O
Which version of gnome-do are you running? I'm running 0.8.2. I can't remember which version added in the ability to change the dock orientation. Originally, you couldn't move it. The bottom was the only position available.

---

### Post by gymophett on 2009-09-20
> **qamelian said:**
> Which version of gnome-do are you running?

I attached a screen shot of me not having the apps folder. 
and 0.8.1.3
Let me upgrade to 0.8.2 quickly and I'll get back to ya.

---

### Post by FuturePilot on 2009-09-20
> **gymophett said:**
> It's amazing how I don't even have that folder. :O

You need to press Alt+F2 and type 
```
gconf-editor
```

---

### Post by gymophett on 2009-09-20
Wait. Upgraded to 0.8.2 and now you can change it via Gnome-Do GUI.
Great work Gnome-Do!
SOLVED.

---

### Post by Mi11z on 2010-09-26
> **gymophett said:**
> Wait. Upgraded to 0.8.2 and now you can change it via Gnome-Do GUI.
Great work Gnome-Do!
SOLVED.

How and i'm trying the earlier method anyway. :)

---

### Post by Mi11z on 2010-09-26
> **qamelian said:**
> You need to launch gconf-editor from Alt-F2. Navigate to ```
/apps/gnome-do/preferences/Docky/Utilities/DockPreferences
``` and locate the Orientation setting in the righthand pane. Change **bottom **to the value you prefer.


I get:

```
/apps/gnome-do/preferences/Docky/Utilities/DockPreferencesbash: /apps/gnome-do/preferences/Docky/Utilities/DockPreferences: No such file or directory

```

:(

*************************************************EDITED************************************************

Yeah SOLVED lol, in the new now current version you can simply drag and drop it to move it. :D

---

### Post by munishvit on 2010-10-15
> **qamelian said:**
> you need to launch gconf-editor from alt-f2. Navigate to ```
/apps/gnome-do/preferences/docky/utilities/dockpreferences
``` and locate the orientation setting in the righthand pane. Change **bottom **to the value you prefer.

+1:p

---

