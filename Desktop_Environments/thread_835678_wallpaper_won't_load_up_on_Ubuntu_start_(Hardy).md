---
title: "wallpaper won't load up on Ubuntu start (Hardy)"
date: 2008-06-20
forum: Desktop Environments
---

### Post by ybd on 2008-06-20
Sorry for a potentially stupid question, but I'm pretty new.

I set my wallpaper as normal, and added shortcuts to drive C and drive D on the desktop (both of which were the original partitions Windows used, not the ones created by the Ubuntu installation)
However whenever I restart Ubuntu, it loads one of the default wallpapers instead and both shortcuts aren't there (but the rest of them are)
Then as soon as I navigate to one of those drives it'll load up the wallpaper I set. Is it because the wallpaper is located in of those partitions?

Thanks for your help.

---

### Post by konungursvia on 2008-06-20
I would copy the image of the wallpaper into the /home/yourname directory, then load it from there in linux. The problem may be that linux is not mounting the foreign drives in time to load the wallpaper.

---

### Post by Happy_Man on 2008-06-20
Also, to let GNOME do the shortcutting for you: Press alt-f2, enter ```
gconf-editor
```, and then go to "apps/nautilus/desktop" and check the volumes_visible option if it isn't already.

---

