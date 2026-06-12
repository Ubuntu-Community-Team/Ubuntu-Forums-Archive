---
title: "pasting stops working when I quit kate/mousepad"
date: 2007-11-11
forum: Desktop Environments
---

### Post by KhaaL on 2007-11-11
I just noticed a very odd thing, when I run a notepad app and copy a string of text, and go to another window to paste it, it will work ONLY if the app is still running... Is this behaviour normal? I'm running KDE by the way.

---

### Post by GeneralZod on 2007-11-11
No, that's not normal - klipper should be handling the clipboard persistence.

Is klipper installed and running?

---

### Post by KhaaL on 2007-11-11
Klipper is usually not running  since I thought that the last copied thing is kept in memory until it's replaced by another string, and that it was handled internally... I guess I shoult put it on autostart again :oops:

---

### Post by GeneralZod on 2007-11-11
> **KhaaL said:**
> Klipper is usually not running  since I thought that the last copied thing is kept in memory until it's replaced by another string, and that it was handled internally... I guess I shoult put it on autostart again :oops:

There are two clipboards, I think: the familar CTRL+C,CTRL+V one, and the highlight,middle-click one used by X.  I think X handles the persistent of the latter sort, but not the former: this is the responsibility of klipper and/ or glipper.

---

### Post by Linicks on 2007-11-11
I fell in the same trap ages ago:

[https://bugs.kde.org/show_bug.cgi?id=137240](https://bugs.kde.org/show_bug.cgi?id=137240)

Nick

---

