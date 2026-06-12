---
title: "Nautilus 3.20 remembers last session"
date: 2016-10-14
forum: Desktop Environments
---

### Post by monkeybrain20122 on 2016-10-14
In Ubuntu 16.10 nautilus has this "feature" of remembering whether hidden files were shown in the last session instead of hiding them by default. Is there a way to restore the old behaviour where hidden files are always hidden by default unless press ctrl+h or choose "show hidden" from menu?

---

### Post by mc4man on 2016-10-14
I don't think so. In the past it was both a nautilus preference & an in nautilus one time action. Now it's a "org.gtk.Settings.FileChooser" setting. So once enabled it stays enabled until disabled no matter how it's enabled. (3 ways, menu, binding, dconf

I guess you could create a binding or context menu option to disable.

---

