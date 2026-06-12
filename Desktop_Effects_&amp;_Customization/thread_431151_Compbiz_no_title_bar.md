---
title: "Compbiz no title bar"
date: 2007-05-02
forum: Desktop Effects &amp; Customization
---

### Post by mhanraha on 2007-05-02
So I enabled my desktop effects and it worked well other than the fact the title bars were gone, and the terminal would just be a large white box.  I then saw this thread [http://ubuntuforums.org/showthread.php?t=416630](http://ubuntuforums.org/showthread.php?t=416630) and tried it, not thinking that it might be different for compbiz.  Since I added that code the cube no longer worked.  Any ideas? thanks
-Mark

---

### Post by scanez on 2007-05-02
Is gtk-window-decorator running?

---

### Post by mhanraha on 2007-05-02
not sure, how would I tell?

---

### Post by scanez on 2007-05-02
Hit <Alt>F2, and enter

gtk-window-decorator --replace

Does this fix the borders?

---

### Post by lawsondba on 2007-05-10
I have same problem.  That does not help.   Most beryl functions are working cube, rain, rotate cube...  Just no title bar, also my terminal windown is white.   xorg.conf looks good.

---

### Post by legendnz on 2008-05-12
That worked for me... thanks.

---

