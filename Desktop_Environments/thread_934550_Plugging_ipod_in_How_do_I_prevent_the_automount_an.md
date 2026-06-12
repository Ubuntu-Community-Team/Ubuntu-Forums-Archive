---
title: "Plugging ipod in: How do I prevent the automount and rhythmbox start?"
date: 2008-09-30
forum: Desktop Environments
---

### Post by Cracauer on 2008-09-30
Since some recent upgrade of my Ubuntu 6.06.2 LTS I get this behavior:

plugging in my rockbox-ified iPod, it gets automounted under /media/ipod-1 and rhythmbox comes up.

I don't want or need this

For the life of me I can't figure out whether udev or some GNOME stuff are doing this. Greg'ing /etc for terms like ipod or rythmbox has proven unfruitful.

Where's that configured?

Thanks

---

### Post by Cracauer on 2008-09-30
OK, as always you find it right after posting.

Looks like GNOME has that configured right in the top-level user-local system configuration. Just killing all the "auto-<anything>" does exactly what I want :)

---

