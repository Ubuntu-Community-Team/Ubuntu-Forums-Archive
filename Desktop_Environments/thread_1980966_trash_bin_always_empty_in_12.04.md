---
title: "trash bin always empty in 12.04"
date: 2012-05-16
forum: Desktop Environments
---

### Post by nkbatsi on 2012-05-16
Hi to all!
Just upgraded to 12.04, but after this my trash bin is always empty, the deleted files seem to be deleted permanently right away (no i did not use<shift+del>).

Any ideas?

---

### Post by wilee-nilee on 2012-05-16
> **nkbatsi said:**
> Hi to all!
Just upgraded to 12.04, but after this my trash bin is always empty, the deleted files seem to be deleted permanently right away (no i did not use<shift+del>).

Any ideas?

Are you choosing move to trash, when you say the "deleted" files it is a bit confusing.

---

### Post by nkbatsi on 2012-05-16
yes i choose "move to trash" but still trash is empty!

---

### Post by nkbatsi on 2012-07-06
Ok I just solved it, I navigated to the trash folder through a terminal using this command:
< ~/.local/share/Trash/files>

Then  did <shift> + <Del> to permanently delete all files and now my trash icon works just fine!

---

