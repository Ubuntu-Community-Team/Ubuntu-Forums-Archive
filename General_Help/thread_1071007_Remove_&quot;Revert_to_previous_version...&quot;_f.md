---
title: "Remove &quot;Revert to previous version...&quot; from Nautilus right click menu?"
date: 2009-02-15
forum: General Help
---

### Post by Hund on 2009-02-15
Hi,

I have installed Deja Dup and since then I have the option "Revert to previous version..." in my right click menu in Nautilus. How can I remove that option from Nautilus?

---

### Post by mc4man on 2009-02-15
I'm assuming you are keeping the app, otherwise just uninstall it.
That would be a nautilus extension, which are stored in 
/usr/lib/nautilus/extensions-2.0/ as .so files. There may be others from 'Deja' but it's the .so that creates the extension

Whether 'disabling' the .so is a good idea, or breaks the app, can't say. (so your on your own there

I wouldn't delete it, either rename or move somewhere safe so you can restore if need be. (At best you may want it in if you do delete the app.

You'd need to do a restart after 'disabling'

---

### Post by Hund on 2009-02-16
Thx! Renaming the file "deja-dup.so" seems to work fine. :) I just restarted Nautilus.

---

