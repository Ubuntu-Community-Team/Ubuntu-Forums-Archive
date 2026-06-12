---
title: "&quot;Appearance&quot; No Longer Opens"
date: 2009-03-17
forum: General Help
---

### Post by jdrom17 on 2009-03-17
To be honest, I have no idea what I did to cause this, but now the Appearance preferences will no longer open. It seems to open but immediately closes itself.

I did install Emerald but it seemed to be working fine after that as I went into the Appearance preferences and changed a few things. However after restarting, I could no longer open either the Appearance or the Emerald Theme Manager. They both seemingly automatically close.

Everything is fine in the Guest account though so I'm guessing somehow a setting somewhere got messed up, but I don't know where to look or what to change.

---

### Post by adult swim on 2009-03-17
if you open a terminal and enter in ```
gnome-appearance-properties
``` does it return any errors?

---

### Post by jdrom17 on 2009-03-18
Yeah it does, all pertaining to missing image files in pixmap_path.

So I re-extracted the theme files and all is fine again :)

Thanks

---

