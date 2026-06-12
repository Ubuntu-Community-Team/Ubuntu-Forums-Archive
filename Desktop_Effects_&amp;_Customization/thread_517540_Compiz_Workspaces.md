---
title: "Compiz Workspaces"
date: 2007-08-04
forum: Desktop Effects &amp; Customization
---

### Post by digital006 on 2007-08-04
I have 4 workspaces and would like to map them to the 4 sides of my Compiz cube, is this possible? Hopefully it is but I'm not sure.

Regards,
Mike

---

### Post by hyperair on 2007-08-04
If you're using Compiz Fusion: In the general settings section of CompizConfig Settings Manager, go to desktop size and set Number of desktops to 1, vertical virtual size 1, and horizontal virtual size 4.

If you're using regular Compiz (Desktop Effects): Go to your configuration editor (Open run dialog and type gconf-editor) and navigate to /apps/compiz/general/screen0/options. On the right panel set hsize to 4, vsize to 1, and number_of_desktops to 1.

---

### Post by digital006 on 2007-08-05
Thank you very much, My compiz fusion is now looking working a lot better.

---

### Post by tmh on 2007-08-12
If I understand correctly, your solution switches from workspaces to viewports. Viewports have the very annoying (to me) property of allowing overlapping windows, which particularly screws up the window list. Is it possible to map *workspaces* onto the cube, so we can have the cool rotation animation without the overlap?

---

### Post by hyperair on 2007-08-12
Nope, anyway I got irritated by the fact that the windows don't overlap. I understand that some may feel differently (i.e. you) but there is currently no possible way (without hacking the whole thing open) to support workspaces around the cube.

---

### Post by ivesjd on 2007-08-12
What do you mean by overlapping windows? If you mean what I think you mean, switching to metacity and then back (for me) brings them back down to just one copy. That is my gDesklets that do that. The other thing is if a window is to far over then it will show up partially on the next side of the cube. When that happens I just go left or right on the cube and move it.

---

