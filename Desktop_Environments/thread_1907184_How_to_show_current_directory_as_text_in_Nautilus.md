---
title: "How to show current directory as text in Nautilus"
date: 2012-01-10
forum: Desktop Environments
---

### Post by vfclists on 2012-01-10
In the Hardy version of Nautilus it is possible to change the directory indicator from the set of buttons to an edit control from which you can copy the whole directory, or change the directory location by typing the directory you want there, much like the 'Display the full path in the address bar option' in Windows.

Somehow this feature seems to be missing from Lucid, or is it simply hidden some where?

---

### Post by erind on 2012-01-10
Maybe this can help: 

Open gconf-editor (Alt+F2 and type *gconf-editor*), navigate to '*apps –> nautilus -> preferences*' and check the box "*always_use_location_entry*".

---

### Post by Krytarik on 2012-01-10
> **erind said:**
> Open gconf-editor (Alt+F2 and type *gconf-editor*), navigate to '*apps –> nautilus -> preferences*' and check the box "*always_use_location_entry*".
Plus, to only temporarily change that style, press Ctrl+L.

Regards.

---

### Post by vfclists on 2012-01-15
Both methods are good, thanks

There used to be something you could click to change the appearance before, wasn't there?

/vfclistsGUY

---

### Post by mcduck on 2012-01-15
> **vfclists said:**
> Both methods are good, thanks

There used to be something you could click to change the appearance before, wasn't there?

/vfclistsGUY

Yes, there used to be a button for that but it was removed from Nautilus at some point. You can still change it through Go->Location... from the menu, though, so there is still a GUI way to do it.

---

