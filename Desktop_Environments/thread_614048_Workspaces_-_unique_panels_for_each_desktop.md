---
title: "Workspaces - unique panels for each desktop"
date: 2007-11-15
forum: Desktop Environments
---

### Post by thelost on 2007-11-15
I would like to set up a different panel (or none at all) for each workspace. This is so that for instance I can can run Virtualbox fullscreen on one of my workspaces without panels getting in the way. I am aware I can set panels to autohide, but the lip of the panel is always poking out and this is pretty irritating.

Could someone tell me if this is possible?

---

### Post by jpietari on 2007-11-17
From what I hear, it is not possible to have different workspaces have different configurations.

---

### Post by Forlong on 2007-11-17
I'm afraid that's not possible but you can set the panel to fully autohide:

Open
```
gconf-editor
```
look for

**/apps/panel/toplevels/top_panel_screen0**

as well as

**/apps/panel/toplevels/bottom_panel_screen0**

and change **auto_hide_size** to **0**

---

### Post by thelost on 2007-11-18
> **Forlong said:**
> I'm afraid that's not possible but you can set the panel to fully autohide:

Open
```
gconf-editor
```
look for

**/apps/panel/toplevels/top_panel_screen0**

as well as

**/apps/panel/toplevels/bottom_panel_screen0**

and change **auto_hide_size** to **0**

That's perfect, thanks!

---

