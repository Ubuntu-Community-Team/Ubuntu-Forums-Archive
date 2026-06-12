---
title: "GNOME thinks the trash isn't empty"
date: 2008-11-20
forum: Desktop Environments
---

### Post by dhuff on 2008-11-20
Under Ubuntu 8.04, if you hover over the trash can icon in GNOME, it thinks there is one item in there. However, if you open the trash, it's empty.

My acct/group is the owner of ~/.local/share/Trash/ and everything under that. Permissions on that directory & its contents are set to 700. An "ls -la ~/.local/share/Trash/files" shows no files.

How do I get GNOME to update the current status of the trash can icon ? :confused:

---

### Post by Tamlynmac on 2008-11-20
I had the same problem. I deleted the trash can and reinstalled from the "Add to Panel" the problem went away with the delete.

---

### Post by dhuff on 2008-11-20
OK, but did the problem reoccur the next time you added files to the trash, then right-clicked on the trash can icon to empty it ?

---

### Post by Tamlynmac on 2008-11-20
No, the problem never resurfaced after replacement. I still don't know what caused it but after replacing, it never occurred again.

---

### Post by dhuff on 2008-11-20
OK, I tried the same thing and it worked. The trash can icon now updates its status when emptied.

Cool, thanks :)

---

### Post by mister_p_1998 on 2010-06-09
So in a console window, I switched to  root and did an rm -R -I for the each of the folders I wanted deleted.   Success!!!
===============


you might find it easier to type sudo nautilus, and browse to the trash folder.
Steve

---

