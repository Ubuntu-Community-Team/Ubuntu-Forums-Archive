---
title: "How to display startup logs when in startup processing"
date: 2009-03-08
forum: General Help
---

### Post by kamusis on 2009-03-08
My Ubuntu 8.10 desktop can't startup, stuck in the startup progress bar screen, How can I see the scroll up logs just like the older linux version.

---

### Post by Elfy on 2009-03-08
Booting recovery mode will show oyu what is going on or you can edit grub at start - press e you should then be in the simple editor - go to end of the kernel line and remove quiet splash, then b to boot iirc

---

### Post by qstraza on 2009-03-08
> **kamusis said:**
> My Ubuntu 8.10 desktop can't startup, stuck in the startup progress bar screen, How can I see the scroll up logs just like the older linux version.


Try hiting ctrl+alt+F2 to change terminal and than login and check dmesg, etc...

---

