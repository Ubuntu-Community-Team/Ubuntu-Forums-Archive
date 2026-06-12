---
title: "How does Nautilus delete files?"
date: 2008-10-26
forum: Desktop Environments
---

### Post by altonbr on 2008-10-26
I'm looking through 'nautilus-2.24.1/src' and see 'nautilus-trash-bar.c'
'nautilus-trash-bar.h' but I can not find where Nautilus actually unlinks data from the hard drive.

I'm looking to implement a secure-delete method, similar to 'srm' or 'wipe' and would like to ingrain inside Nautilus.

---

### Post by Ferrat on 2008-10-26
Otherwise there are some scripts out there that does secure delete for nautilus

---

### Post by bapoumba on 2008-10-27
Moved to Desktop Environments.

---

### Post by altonbr on 2008-10-28
GIO/gVFS probably handles this, correct?

---

