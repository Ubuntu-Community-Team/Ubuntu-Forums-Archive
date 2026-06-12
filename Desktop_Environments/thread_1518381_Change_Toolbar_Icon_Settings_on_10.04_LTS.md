---
title: "Change Toolbar Icon Settings on 10.04 LTS"
date: 2010-06-26
forum: Desktop Environments
---

### Post by volobiz on 2010-06-26
I have installed the new Ubuntu 10.04 LTS and do not see where I can change the toolbar icon settings such that I only display icons, not text labels beside the icons. Does anyone know how to fix this?

---

### Post by volobiz on 2010-06-27
Here's the answer. Rightclick the logo next to the Applications menu and choose Edit Menus. Go down to System Tools and check off Configuration Editor. This is basically a tool called gconf-editor. Click Close and then choose that menu item from the Applications\System Tools menu.

Now this is sort of like a Registry Editor if you are familiar with Windows. Expand to this path:

/desktop/gnome/interface/toolbar_style   

In the value you see for "toolbar_style", double click it and type in a new value of "icons". Click OK and then click the X to exit the Gconf-Editor application.

Now your menus will be only icons.

Why the GNOME team decided to not make a control panel item to manage this in standard Ubuntu 10.04 LTS, I'll never know. It was in Ubuntu 8.04 LTS, previously.

---

### Post by vamega on 2010-08-27
I think it's been removed by Ubuntu.
As far as I know, GNOME still has this option.

EDIT: I was wrong. The GNOME team did infact remove this option.

---

