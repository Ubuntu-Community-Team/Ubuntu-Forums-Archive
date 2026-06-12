---
title: "Disabling document tracking in Gnome"
date: 2005-02-11
forum: Desktop Environments
---

### Post by HaloGray on 2005-02-11
Remember to 'clear recent documents' is getting to be a pain.  How can I at the very least remove that from the gnome menu?  At the very best, how can I disable any document tracking at all?

Now excuse me while I go get fitted for my tinfoil hat.

---

### Post by macewan on 2005-02-11
my guess would be to possibly chown of .recently-used or chmod it so you can't write to the file

---

### Post by macewan on 2005-02-11
chmod +400 .recently-used

to change it back so that it works again you switch to +600

chmod +600 .recently-used

---

