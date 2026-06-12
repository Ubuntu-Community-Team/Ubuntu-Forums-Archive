---
title: "No window boarders, Intel Mobile 915"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by Fylk on 2007-04-25
Ok, so I have a Mobile 915GM/PM/GMS/910GML GPU on my laptop. When a load up beryl, I'm completely lacking in window boarders. I've tried both GTK and emerald. 

Ideas?

---

### Post by jordanmthomas on 2007-04-25
just a guess, but maybe delete your emerald settings?
```
rm -r ~/.emerald
```
and then try again.

Also, make sure there aren't any rogue emeralds running before you try:
```
killall emerald
```

---

### Post by Fylk on 2007-04-26
But its a fresh install. Should I have issues with my emerald settings?

---

### Post by jordanmthomas on 2007-04-26
probably not...

---

### Post by csaldan on 2007-04-26
im having the same problem too

---

### Post by Fylk on 2007-04-26
Never mind, now its back to the now border dealie.

---

### Post by hette on 2007-04-26
I'm having this problem with my NVidia Geforce4mx only when I set the rendering path to 'Texture From Pixmap' or 'Automatic'. The problem does not occur when using 'Copy'.

---

### Post by tehbeermang on 2007-04-26
I have the same problem, but only on maximized windows, or windows that span the width of the desktop. Moving just one pixel in replaces the borders.

---

