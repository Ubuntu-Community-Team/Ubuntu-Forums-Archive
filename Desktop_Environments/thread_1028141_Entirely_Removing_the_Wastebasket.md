---
title: "Entirely Removing the Wastebasket"
date: 2009-01-02
forum: Desktop Environments
---

### Post by stderr on 2009-01-02
Is there any simple way to remove the concept of a wastebasket from Ubuntu? I reckon it's in Nautilus.

There is an option in Nautilus preferences to include a delete command that bypasses the wastebasket. 

However, I don't want to use the wastebasket at all. Therefore, I could 'clean things up' a bit too by removing the Move to Deleted Items option in the right click menu, the link to trash:/// under the Deleted Items bookmark, and all the .Trash folders under each partition.

Is there a gconf key, settings file, or something somewhere that gives this option? 

If there isn't, is there just any reasonably simple way to achieve using delete as the default action? 

If not, no big problem; I don't mind the CLI :)

---

### Post by Ben Page on 2009-01-02
There is an option in nautilus under edit - preferences - tab: behaviour, to add a delete option in the right click menu so you can delete files without putting them in the bin. You can remove the bin from the desktop by using ubuntu tweak tool. This way you will remove trace of the bin, but to completly remove the bin for "real", **i think** it is imposible, like in windows, you can turn it of, bu os will create hidden recicled folder on each partition (fortunateli 1 or 2 KBs size).

---

### Post by stderr on 2009-01-02
Ah, Ubuntu Tweak - I've heard of it, but never tried it before. Sounds like it'll get me a little closer to my goal :) Cheers

---

