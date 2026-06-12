---
title: "Mounted Drive Icons"
date: 2009-05-13
forum: General Help
---

### Post by ebanlague on 2009-05-13
Alright, I have a USB HDD hooked up to my computer all the time.

I guess I'm just wondering if it is possible to have the drive mounted without it appearing on the Desktop. I try to keep a totally empty desktop (Love for my Wallpaper!) and I do frequently use the drive. Unmounting it constantly gets very annoying.

Thanks, Evan.

---

### Post by ebanlague on 2009-05-13
Anyone? This would be greatly appreciated.

[shameless bump :p]

---

### Post by gamblor01 on 2009-05-14
Open a terminal and type in:

```

gconf-editor

```

Then click on apps -> nautilus -> desktop.  There should be an option in there that says "volumes_visible".  Just remove the checkbox from there and it should hide the mounted volumes on your desktop (i.e. no longer show them).  Enjoy!

---

### Post by ebanlague on 2009-05-14
That worked, thanks so much!

---

### Post by bran on 2009-05-25
> **gamblor01 said:**
> Open a terminal and type in:

```

gconf-editor

```

Then click on apps -> nautilus -> desktop.  There should be an option in there that says "volumes_visible".  Just remove the checkbox from there and it should hide the mounted volumes on your desktop (i.e. no longer show them).  Enjoy!

Thanks hugely  i needed this too.

Bran

---

