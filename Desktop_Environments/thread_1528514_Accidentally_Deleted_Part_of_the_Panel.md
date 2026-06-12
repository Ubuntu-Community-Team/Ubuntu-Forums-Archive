---
title: "Accidentally Deleted Part of the Panel"
date: 2010-07-10
forum: Desktop Environments
---

### Post by ChildOfLore on 2010-07-10
I didn't delete the whole panel, but just the bit where it shows icons of currently running programs. So now when Ktorrent, Kalarm or Desktop Drapes are running I can't see their icons on the panel and I can't find how to add the thing I've deleted from the "Add to Panel" menu. Anyone know how to get it back?

Thanks,
Marlon

---

### Post by chiliman on 2010-07-10
I believe what you are talking about is called "Notification Area"

You should be able to right click the panel, select add to panel, and select notification area, then click add.  you can also use that search bar in the window that opens if your having trouble finding it.

---

### Post by ubunterooster on 2010-07-10
Add to panel "window list"

---

### Post by Pizack on 2010-07-11
This seems to happen quite a bit.  Perhaps it should be in an FAQ somewhere?

---

### Post by tjandracom on 2010-07-11
you could run this script to make the panel locked down (to prevent it from accidentally deleted). this is a mandatory setting that affect all users and need sudo.

```

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type bool --set /apps/panel/global/locked_down true

```

if u want to add something to your panel, you can unlock it with this script:

```

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --unset /apps/panel/global/locked_down

```

---

