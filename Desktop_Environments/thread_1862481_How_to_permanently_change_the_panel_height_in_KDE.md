---
title: "How to permanently change the panel height in KDE?"
date: 2011-10-16
forum: Desktop Environments
---

### Post by bobtestact on 2011-10-16
Whenever I change the height of the KDE panel, the new height lasts until I log out.  When I log in again, the panel reverts back to its old size (which I think is 32 pixels tall for my theme, "Air for netbooks").

Is there a way to permanently save the new panel height so that it's applied automatically on the next login?

Can I edit a configuration file to control this?

Is there something I can run upon login that can programmatically change the height of the panel?

---

### Post by lovinglinux on 2011-10-16
It as bug. Try to delete the panel and create a new one. If that doesn't help, you might need to delete the plasma config file.

---

### Post by bobtestact on 2011-10-17
Thanks.  Creating a new panel solved the problem.

This suggests that the panel size is being stored in a configuration file somewhere.  Does anyone know the location of that config file?

---

### Post by lovinglinux on 2011-10-17
> **bobtestact said:**
> Thanks.  Creating a new panel solved the problem.

This suggests that the panel size is being stored in a configuration file somewhere.  Does anyone know the location of that config file?

They are stored under ~/.kde/share/config/plasma...

---

