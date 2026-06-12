---
title: "can't change fonts"
date: 2006-02-13
forum: Desktop Environments
---

### Post by xerosis on 2006-02-13
i've just installed kde, then removed it (sorry kde fans :p) but somehow this has made gnome reset to using it's default font sizes even though the settings are different. i run kwin as WM but i don't think this should matter, any ideas?

---

### Post by escape on 2006-02-13
I'm having the exact same problem. System fonts are a size or two too big, and I can't find a way to change them. They're also a bit blurry now...

---

### Post by bluevoodoo1 on 2006-02-13
system > preferences > font

will that help with anything???

---

### Post by xerosis on 2006-02-14
the settings are fine, they remain unchanged from before just the actual fonts have changed. if i change the font size to something like 20pt they still don't change anymore.

---

### Post by anllogui on 2006-02-14
It is probably that you have installed and used the gtk-qt-engine. It creates a file in your home called something like .gtkrc or similar. If you read it, you can find a note that says that it is created by KDE or by the engine. If you find it, remove the file and restart the gdm.
You will find the gnome fonts and will get once more the control of the fonts type and size.

---

### Post by xerosis on 2006-02-15
i couldn't find the file, i think you're on the right lines though.

---

### Post by farish on 2006-10-29
I had this problem after upgrading to Edgy.  Deleting the .gtkrc file fixed it.  Thanks!  (It was driving me batty!)

---

