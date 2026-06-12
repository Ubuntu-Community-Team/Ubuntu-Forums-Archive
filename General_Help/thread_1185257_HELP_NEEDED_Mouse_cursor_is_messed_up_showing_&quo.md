---
title: "HELP NEEDED: Mouse cursor is messed up showing &quot;busy&quot; by default."
date: 2009-06-12
forum: General Help
---

### Post by MoToR on 2009-06-12
Hello, everybody,

After a recent abnormal shutdown caused by a power outage the mouse cursor in my Ubuntu Jaunty shows "busy" status by default, i.e. it's a round roller and not a usual arrow.

When the system powers up, the cursor appears as an arrow for a few moments, but when the desktop starts to show up the cursor switches to roller and stays that way.

The cursor changes its shape properly (shows like arrow or text cursor) within applications like firefox, terminal, unless I point at their title bar, where the cursor changes back to "busy" status and stays that way on the desktop, in menus or other generic GUI elements. 

Any advice how to fix this issue will be highly appreciated.

---

### Post by MoToR on 2009-06-22
^ bump ^

---

### Post by MoToR on 2009-06-22
When nobody's helpful - help yourself.

I searched for any corrupted configs throughout my Home Folder and accidentally solved the problem I had by deleting everything inside the
**~/.config/gnome-session/saved-session/**
folder.

Case closed.

---

