---
title: "Just got a cursom theme"
date: 2009-12-01
forum: Desktop Environments
---

### Post by coolranch on 2009-12-01
I just went and got this cursor theme.

[http://gnome-look.org/content/show.php/GT3?content=106536](http://gnome-look.org/content/show.php/GT3?content=106536)

it is really nice, but I dont understand why it disappears when I leave my web browser. It goes back to the original white icon when I mouse back over to a web page it comes back, It is quite annoying haha.

---

### Post by smani on 2009-12-01
See [http://en.opensuse.org/Compiz_Troubleshooting](http://en.opensuse.org/Compiz_Troubleshooting) last section (Unable to change cursor theme), there are also many other forum posts / bug reports concerning this bug with suggested workarounds.

---

### Post by Hero of Time on 2009-12-01
Sometimes you need to log out and back in before the cursor theme is completely set. I always select Default as theme, install cursors in /usr/share/icons and put the cursor name in /usr/share/icons/default/index.theme. This is the contents of the file:
```
[Icon Theme]
Inherits = Point-Black-Small
```
The name must be the same as the folder name that holds your theme.

My method makes the cursors available for the whole system, not just the user.

---

### Post by coolranch on 2009-12-01
> **Hero of Time said:**
> Sometimes you need to log out and back in before the cursor theme is completely set. I always select Default as theme, install cursors in /usr/share/icons and put the cursor name in /usr/share/icons/default/index.theme. This is the contents of the file:
```
[Icon Theme]
Inherits = Point-Black-Small
```The name must be the same as the folder name that holds your theme.

My method makes the cursors available for the whole system, not just the user.


This worked haha.

Logged out last night, then back in this morning and it is working great, thanks for the help!

---

