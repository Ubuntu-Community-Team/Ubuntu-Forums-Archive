---
title: "Enable Desktop Effects in non-root user"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by Sid59 on 2007-10-22
Hello All ...

I'm probably missing a setting or something but i can get desktop effects to work under the root/adminstrator account on my install of 7.10.

I'm rolling out new users on this computer but an error pop up says "Desktop Effects could not be enabled".

What am I missing? It works in my personal account but on this other user account (non admin) it's not working.

---

### Post by BungaMan on 2007-10-23
check what the command is for the desktop effects and run that command in a terminal.  Hopefully it will give you output that explains a bit.

ex. run "compiz --replace &" in a terminal and see how that turns out.  If it fails run "metacity --replace &" in the terminal to return back to the normal desktop without effects.

---

