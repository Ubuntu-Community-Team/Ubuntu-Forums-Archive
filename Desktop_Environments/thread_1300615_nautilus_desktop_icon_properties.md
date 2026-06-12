---
title: "nautilus desktop icon properties"
date: 2009-10-25
forum: Desktop Environments
---

### Post by pataphysician on 2009-10-25
I have a few icons on my desktop that I'd like to resize. I've tried "stretching," but it's difficult to get them to be the same size. Is there a text file or some place in gconf that i can numerically set the size of *just* these icons? I know I can set the "default zoom level," in nautilus, but that resizes all icons, which I don't want to do.

Related, I have some folders that I've put "emblems," on. I switched icon sets and deleted the previous icon set I was using. The new icon set doesn't have as many emblems available as the old one. Now some of my folders have file-type looking emblems. I guess when it couldn't find matching emblems in the new icon set, it reverted to the closest icon with a similar name. When I bring up the folder's properties, none of the available emblems are selected, so I can't uncheck anything to remove the current emblem. So again, is there any text file, gconf property, or anything like that where i can manually remove the reference to the folder's emblems?

---

### Post by roggenschrotbrot on 2009-10-25
In gconf-editor change the value of /apps/nautilus/icon_view/default_zoom_level. Possible Values I know of are small, standard and large.

---

### Post by pataphysician on 2009-10-25
> **roggenschrotbrot said:**
> In gconf-editor change the value of /apps/nautilus/icon_view/default_zoom_level. Possible Values I know of are small, standard and large.

Thanks for the reply, but unfortunately doing that is the same as setting the default zoom level in Nautilus' preferences -- it resizes all icons. I only want a few of the icons on my desktop to be resized, while keeping all others at the default size. I kind of just want to "stretch," these few particular icons, but to all the same size, which is tough with the arbitrary drag-resize available on the desktop. I was kind of hoping the size (and emblems) was stored as text values somewhere that I could edit manually on a per-icon basis.

I know it's pretty picky, but I figured I'd ask.

---

