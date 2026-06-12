---
title: "[SOLVED] I installed Soldat.exe using Wine, but I can't find it."
date: 2007-06-02
forum: Gaming &amp; Leisure
---

### Post by RonB123123 on 2007-06-02
I installed Soldat.exe using Wine, but I can't find it.

I looked everywhere for drive_c but I can't find it. Does anyone know where installation files are stored after installing an app using Wine?

Thank you.

~Ron

---

### Post by hikaricore on 2007-06-02
~/.wine/drive_c/Program Files

---

### Post by Sammi on 2007-06-02
Wine created a fake C: drive in you user directory. Full path should be /home/username/.wine/drive_c

From there Soldat should be found in the same place it's found in Win.

---

