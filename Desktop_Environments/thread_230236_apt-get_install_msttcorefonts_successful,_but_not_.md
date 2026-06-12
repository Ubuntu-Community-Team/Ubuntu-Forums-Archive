---
title: "apt-get install msttcorefonts successful, but not seen in OpenOffice"
date: 2006-08-05
forum: Desktop Environments
---

### Post by godtvisken on 2006-08-05
I did `apt-get install msttcorefonts' and it installed ok, (in fact it said it was already installed with the newest version) but in OpenOffice I don't see any of the fonts like Times New Roman and such.. what can I do?

---

### Post by Jagot on 2006-08-05
You could try rebuilding the font information cache files.  From Terminal:

```
sudo fc-cache -f -v
```

---

### Post by godtvisken on 2006-08-05
Sweet! Thanks!

---

