---
title: "Gnomenu key binding"
date: 2009-04-30
forum: Desktop Environments
---

### Post by trypt on 2009-04-30
SOLVE -->

to remove the <super key> binding
had to run:

sudo gedit /usr/lib/gnomenu/Setting_default.xml
   edit the section #Win key activation
                           <SuperL Enable="1"/>
   change "1" to "0"

if that didn't do it, like for me, had to change

sudo gedit /usr/lib/gnomenu/GnoMenu_Object.py
   edit the section #HotKey  Menu Activation
                          if Images.SuperL == "1"
   change "1" to something other than "1" or "0" EX:"10"

that solved the entire key binding problem that was interacting with compiz.

---

### Post by rich.bae on 2009-04-30
You'd better use gnomenu 1.8.
If you want to know more, then visit [https://launchpad.net/gnomenu/+announcements](https://launchpad.net/gnomenu/+announcements).

---

