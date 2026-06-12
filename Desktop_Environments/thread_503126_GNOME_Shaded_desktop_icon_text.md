---
title: "GNOME: Shaded desktop icon text?"
date: 2007-07-17
forum: Desktop Environments
---

### Post by ThinkBuntu on 2007-07-17
Anyone who's used or seen Xfce knows that on the desktop, Xfce icons have a translucent color behind their text. This makes your filenames easy to read regardless of how bizarre a background might be. How can I make my icons do this in GNOME?

---

### Post by jim_p on 2007-07-17
I think you mean this...
[http://ubuntuforums.org/showthread.php?t=89197](http://ubuntuforums.org/showthread.php?t=89197)

The soft semitransparent color can be achieved by altering the 
```
NautilusIconContainer::normal_alpha = Z
``` variable (ranging from 0 to 255)
and the color using 
```
text[NORMAL] = "#YYYYYY"
``` (color in hex mode)

---

### Post by ThinkBuntu on 2007-07-18
Cool. Thanks! *Bookmarks for later*

---

