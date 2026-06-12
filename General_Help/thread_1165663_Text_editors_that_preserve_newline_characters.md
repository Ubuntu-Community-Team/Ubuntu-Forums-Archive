---
title: "Text editors that preserve newline characters"
date: 2009-05-20
forum: General Help
---

### Post by rCXer on 2009-05-20
Is there a text editor that preserves the newlines chars of files?  I am working with DOS files and I want to avoid using unix2dos with gedit.

---

### Post by geirha on 2009-05-20
vim and gvim will preserve '\r\n'-endings if the file you edit already have them, and if you want to create a new file using '\r\n' by default, then type in ```
:set fileformat=dos
``` and start editing.

Though, vim is a bit different than gedit, and requires a bit of getting used to if you haven't used it before.

EDIT: It's been added to the wishlist for gedit btw. [https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/197028](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/197028)

---

### Post by rCXer on 2009-05-20
Are there any simpler ones with tabs like gedit?

---

