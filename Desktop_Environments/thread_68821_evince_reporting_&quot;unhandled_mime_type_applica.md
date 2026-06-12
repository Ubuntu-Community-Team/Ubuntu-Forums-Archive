---
title: "evince reporting &quot;unhandled mime type: application/x-extension-pdf&quot;"
date: 2005-09-24
forum: Desktop Environments
---

### Post by qubit on 2005-09-24
Evince is failing to open any PDFs, giving me an error "Unable to open document, Unhandled mime type: application/x-extension-pdf".  The only place I can find a reference to this non-standard mime-type is in my ~/.local/share/applications/mimeinfo.cache, and if I remove it, Gnome automatically adds it back.

How do I fix/bypass this?

---

### Post by heroedeleyenda on 2007-06-29
Hi,
Reinstalling shared-mime-info ( v0.18 ) solve my pdf handling problem.
But I also have a problem with gthumb thumbnails. I am looking for the fix.
Regards

---

### Post by adza on 2007-10-11
wow, excellent... i also was having this problem (experienced after removing beryl for compiz fusion)... thanks for the post!! **kudos** :)

---

