---
title: "Dropdown Menu shadows with RGBA and Compiz"
date: 2010-07-01
forum: Desktop Environments
---

### Post by steveneddy on 2010-07-01
It took me a while and maybe someone else already know this, but I recently added RGBA to give me more transparency.

But when I did this the shadows on the dropdown menus on the panel and in nautilus were not shadowed.

To correct this in Compizconfig Settings Manager:

Turn on Window Decoration is you haven't already.

Copy/Paste this line in the Shadow Windows info box:
  
  > any (class=Tooltip | Menu | PopupMenu | DropdownMenu | Unknown)

That should be enough to get your drop shadows back on the drop down menu items. worked for me.

Even works on the menus in Chromium even if the GTK themes window border is off, but is still won't shadow the window if GTK window borders are turned off.

Hope this helps someone.

---

### Post by frankob on 2010-07-12
Thank you very much for this trick!

I can live without gtk-rgba, but not without shadows in Gnome. Now I have both. :-)

---

### Post by frankob on 2010-07-12
I just noticed that this way I lost the shadows under menus in OpenOffice.org. But it is easaly solvable.

Instead of "any (class=Tooltip | Menu | PopupMenu | DropdownMenu | Unknown)", in the in the Shadow Windows info box should be
```
any | (class=Tooltip | Menu | PopupMenu | DropdownMenu | Unknown) 
```
(notice the vertical separator line between "any" and "(class=Tooltip")

---

### Post by frankob on 2010-07-13
Actually, I found out that the solution I gave above draws shadows even under invisible windows, which sucks very much if you are using Cairo Dock, Gnome-do and similar stuff... And steveneddy's solution doesn't draw shadows under Gnome Panel nor OpenOffice.
So I found out a better solution, after a couple hours of research. Actually, with the rgba module on, the Compiz shadow settings act really weird, but I finally found a good solution. At least for me...

In "Shadow windows" I added:
```
(type=Tooltip | Menu | PopupMenu | DropdownMenu | Unknown) | name=gnome-panel | name=gkrellm | name=VCLSalFrame
```

I guess everything is clear until "name=VCLSalFrame". That is the "name" of OpenOffice windows. It adds shadows to the OpenOfffice menus. :-)

Somebody will notice I could have given just a type for "Dock" and have both Gnome Panel and Gkrellm shadowed. But then it gives shadow also to Cairo-Dock, as it is, obviously, recognaized as a dock,too, and that is not really nice. This way I keep my Cairo-Dock unshadowed.

Practically, you have to specify what to shadow. "any" is not enough. But if you specify what not to shadow, even just one thing, it all falls back to default, and there is no effect whatever else you do in that field... So you have to specify exclusively what you DO want to shadow, and hope that it will do the trick.

Hope this helps somebody.

---

### Post by Milos_SD on 2010-07-13
Where is that "Shadow windows" option? I can't find that in ccsm.

---

### Post by frankob on 2010-07-13
Effects > Window Decoration, the last line.

---

### Post by digitalcitizenx on 2010-07-16
It is entirely possible that the OP did not want shadows on the panel or in Open Office.

My personal preference is no shadows on the panel OR in Ooo.

These are great references though on the set up of that text file.

---

### Post by bilalsana on 2010-11-20
Thank you so much....i was so much annoyed on losing those shadows!They are finally back and i luv em! :)

---

### Post by mohave on 2010-12-11
Thank you for sharing, I wasn't sure to find any answer to this subtle issue!

---

### Post by frankob on 2011-01-27
I am glad I could help. :-)

---

### Post by dzadze on 2011-09-05
i still have no shadow under desktop right click menu, i have 11.04 ubuntu.

---

### Post by muralive on 2011-10-23
Thank you for putting the effort to share this info, it keeps helping others.

---

