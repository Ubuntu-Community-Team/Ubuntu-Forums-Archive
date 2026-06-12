---
title: "XFCE ugly switcher icons"
date: 2013-04-28
forum: Desktop Environments
---

### Post by mreq on 2013-04-28
Many apps in the switcher don't use my theme's icons (Faenza).

[ATTACH=CONFIG]241909[/ATTACH]

They are working fine (see Plank screenshot) everywhere else.

[ATTACH=CONFIG]241908[/ATTACH]

How can I force XFCE switcher to use my theme's icons?

EDIT: Is there a way how to tell the switcher I don't want those fancy mini-previews from Evince, GIMP, ristretto etc. but would prefer the app icon?

---

### Post by Frogs Hair on 2013-04-28
If you can enter icon properties you can navigate to any folder you want and select an image . Most docks allow this but the images may be coming a folder like pixmaps and those images can be changed root permission in the file system but will revert if application is updated. I am not logged itno XFCE at the moment but do use it.

---

### Post by mreq on 2013-04-28
> **Frogs Hair said:**
> If you can enter icon properties you can navigate to any folder you want and select an image . Most docks allow this but the images may be coming a folder like pixmaps and those images can be changed root permission in the file system but will revert if application is updated. I am not logged itno XFCE at the moment but do use it.

Thanks for reply! Not sure, if we understand each other. The dock icons are the right ones.

---

### Post by Frogs Hair on 2013-04-28
Sorry , After looking at the picture again you do have some faenza icons in the switcher. The ones that don't match are comming from a different folder. Pixmaps ?

---

### Post by Frogs Hair on 2013-04-28
There are questions on this subject going back to 2009 at least  and there are no solutions that I can find . Locating and changing the images may be the only way.

---

### Post by mreq on 2013-04-28
Well that's a bummer. Search for **terminator** in **/usr/share/icons** leads to **hicolor** theme. I'll try to back it up and copy/overwrite it with the Faenza one.

---

### Post by mreq on 2013-05-17
That's strange. I successfully overwrote terminator icons and get the nice one in switcher. However, overwriting all instances of Clementine icon leads nowhere. Hate to, but have to let it go.

---

