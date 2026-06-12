---
title: "Missing trash icon on desktop"
date: 2005-06-26
forum: Desktop Environments
---

### Post by krist on 2005-06-26
Hi,

The trash icon on my Hoary 5.04 stock Gnome 2.10.0 desktop is gone. The applet in the taskbar is still working, but I want the desktop icon back :)

The strange thing is that the Computer, Home and all shared folder's icons are still there, also all *_icon_visible checkboxes in the config editor (/apps/nautilus/desktop) are switched on. I've already tried to switch them on and off while logging off and back on again. Nothing.

It must have disappeared while trying some themes. But reverting everything back to default and deleting all custom themes didn't help.

Any ideas?

---

### Post by manicka on 2005-06-26
go to 

Applications --> System Tools --> Configuration Editor
Click on Apps--> Nautilus -->desktop

and check  trash_icon_visible

---

### Post by thagame on 2005-06-27
read his whole post. he said he did all taht.

---

### Post by krist on 2005-06-28
I've found it, it was there but out of reach.

I used to have the trash icon in the bottom right corner of the desktop. As I was tweaking my desktop settings I also switched to a lower screen resolution for a while. When I switched back the trash icon somehow got stuck out of the screen because it was on the invisible part of the virtual desktop while doing so (I hope you get what I mean :)).

So all I needed to do was sort the icons by name from within the desktop's context menu and voilà there it was.

---

