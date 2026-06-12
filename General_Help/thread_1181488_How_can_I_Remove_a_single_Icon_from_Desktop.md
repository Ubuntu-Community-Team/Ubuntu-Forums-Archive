---
title: "How can I Remove a single Icon from Desktop?"
date: 2009-06-08
forum: General Help
---

### Post by toejamfootball on 2009-06-08
Hi!

I love having my HDDs etc. Icons visible on the Desktop when mounted, but I really do not like the iPod Icon being there.

Is it possible to choose which drives display Icons on the Desktop?

Thanks :)

---

### Post by toejamfootball on 2009-06-08
Does anyone have any ideas? I thought that I could add a key in apps->nautilus->desktop using gconf-editor, but I am not sure what to call it and how to set it up properly.

---

### Post by Legace on 2009-06-08
Try to mount the iPod to somewhere else than /media.

---

### Post by toejamfootball on 2009-06-08
> **Legace said:**
> Try to mount the iPod to somewhere else than /media.
:D I didn't even think of this, thanks.

I can't figure out how to do this :(

---

### Post by Legace on 2009-06-08
Ignore. I don't think it'll work for USB devices.

---

### Post by CatKiller on 2009-06-08
There is a slightly messy way to do this. You could unset the /apps/nautilus/desktop/volumes_visible in gconf-editor so that no removable media gets shown on the Desktop, and then create launchers for ```
nautilus /media/wherever
``` on the Desktop for the drives that you do want to see.

---

### Post by toejamfootball on 2009-06-08
> **CatKiller said:**
> There is a slightly messy way to do this. You could unset the /apps/nautilus/desktop/volumes_visible in gconf-editor so that no removable media gets shown on the Desktop, and then create launchers for ```
nautilus /media/wherever
``` on the Desktop for the drives that you do want to see.
Great, this is perfect! I have set the launchers to Location, /media/(harddrives)

Thanks very much CatKiller!

---

