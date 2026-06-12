---
title: "Compiz Won't Register Mouse Clicks (Sometimes)"
date: 2008-12-15
forum: General Help
---

### Post by Kinetic Being on 2008-12-15
I changed the keybinding for cube rotation in compiz settingsmanager to ALT-MOUSEBUTTON1, and from then on I am not able to click on anything with the right mouse button without it just dragging the window. I was able to access the panel, but not any windows I had open, except for the terminal where I did "metacity --replace" to get my mouse working again, but I want to get Compiz working again...

Anybody have any clues as to what it is?

 I'm thinking it might be that somehow the action for the left mouse button was changed in Compiz when I said 'yes' to disabling the window-move binding that was attached to the ALT-BUTTON1 combo...But I don't know how to change that back, any help is appreciated...

---

### Post by gettinoriginal on 2008-12-22
In the CompizConfig Settings Manager, each setting has a little broom icon, that resets it to default.  Go to the two things you changed and reset the default.  :P

Or you can set the complete Compiz settings back to default by typing into terminal:

gconftool-2 --recursive-unset -a /apps/compiz

---

