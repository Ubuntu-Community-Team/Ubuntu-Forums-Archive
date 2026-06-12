---
title: "[SOLVED] removing the shadow on the font for desktop icons"
date: 2007-11-19
forum: Desktop Effects &amp; Customization
---

### Post by unebaguettesvp on 2007-11-19
does anybody know how to alter the font for the desktop icons in gnome?! specifically, how do you remove the shadow from the font for those icons? change the color?

thanks!

---

### Post by unebaguettesvp on 2007-11-20
found the solution! i had to add this to my gtkrc file!

```
NautilusIconContainer::frame_text	= 1
NautilusIconContainer::normal_alpha	= 0
```

fount this here: [http://ubuntuforums.org/showthread.php?t=89197]("http://ubuntuforums.org/showthread.php?t=89197")

---

