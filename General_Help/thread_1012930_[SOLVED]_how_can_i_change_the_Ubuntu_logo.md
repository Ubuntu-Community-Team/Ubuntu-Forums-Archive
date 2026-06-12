---
title: "[SOLVED] how can i change the Ubuntu logo?"
date: 2008-12-16
forum: General Help
---

### Post by Dadsgé on 2008-12-16
i want to change my menu icon into a 3D icon
i've already tried it once
it worked then, but i've reinstalled 8.04 and now i cannot change it the way i did it before

i used the gconf-editor, navigated trough the files to the menu object
(apps > panel > objects > object0)
the previous time there was an option, use_custom-icon, and then i could change the icon by clicking on 'custom_icon' and then 'edit key'
but now that option is not there anymore...

i even tried to change the icon at ~/.icons but that doesn't work either...

what can i try even more?

---

### Post by Dadsgé on 2008-12-16
ok, i've tried a bit and i found it
so just ignore this post :p
(thanx if you have been thinking about it)

---

### Post by ellalan on 2008-12-16
> **Dadsgé said:**
> ok, i've tried a bit and i found it
so just ignore this post :p
(thanx if you have been thinking about it)
Glad to hear that you found a solution but if you post how it was done it'll be more useful for others as well.

---

### Post by Dadsgé on 2008-12-16
sorry, forgot it
well, i tried it another way
by adding my logo to the used icon theme
i did had some trouble with the background, but that is easy to solve with gimp

so, if you have your logo, just search it (search the icon it will replace, in this case: the menu ubuntu icon) in /usr/share/icons
then copy that name and add your own logo to ~/.icons/[current icontheme]/scalable/places
normally if you use the name 'start-here.png' it will replace the menu icon

this is also an easy way to replace all kinds of icons, you just have to find the name of the current icon

firefox for example, can be replaced by adding your icon to the theme at /128x128/apps and using the name 'firefox-icon.svg'.

and this is something you can easy backup :)

---

