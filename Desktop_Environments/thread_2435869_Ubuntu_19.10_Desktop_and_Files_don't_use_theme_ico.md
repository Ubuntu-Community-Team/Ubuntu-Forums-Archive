---
title: "Ubuntu 19.10 Desktop and Files don't use theme icons"
date: 2020-01-27
forum: Desktop Environments
---

### Post by mazz0 on 2020-01-27
I just installed Ubuntu 19.10 (upgraded from 18.04).  My Desktop and the Files app no longer use the icon theme I select in Tweaks.  Is there a new way to set these?

---

### Post by Frogs Hair on 2020-01-28
You should be able to right click the Icon,select  properties, icon image, and navigate to the desired icon. You could also install the dconf editor and navigate to org>gnome>desktop>interface>icon theme and make sure it matches the icon selection in Tweaks.

---

### Post by mazz0 on 2020-01-29
Yeah, they match.

I've tested different themes and some work as expected, others don't (Example: Numix-Circle works, Numic-Circle Light doesn't - it displays some dark, greyscale icons in Files instead of the pretty Numix style ones).  It's possible there are versions of these icon packs for 19.10 that simply contain different (and incongruous) icons, I suppose, and I'm simply seeing a bad version of the packs now that I've upgraded  Is it also possible that the place Files looks for certain icons has changed and some icon packs need updating?

---

### Post by Frogs Hair on 2020-01-29
> [COLOR=#000000]now that I've upgraded Is it also possible that the place Files looks for certain icons has changed and some icon packs need updating?[/COLOR]

It's hard to say with 3rd party icon themes. If you are using the Numix project ppa you would have the latest version.

[https://github.com/numixproject/numix-icon-theme-circle](https://github.com/numixproject/numix-icon-theme-circle)

---

