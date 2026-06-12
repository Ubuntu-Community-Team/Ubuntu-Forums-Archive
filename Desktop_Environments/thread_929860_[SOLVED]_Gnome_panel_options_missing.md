---
title: "[SOLVED] Gnome panel options missing"
date: 2008-09-25
forum: Desktop Environments
---

### Post by CLomax on 2008-09-25
I could never find anyone with this problem. When right clicking a Gnome panel, the only options I get are 'Help' and 'About Panels' as opposed to applets, options to delete and add panels etc...

Thanks for any suggestions.

---

### Post by Tamlynmac on 2008-09-27
It sounds as if your panel lock is on. To check and change:
Open your gnome configuration editor (gconf-editor)

app/panel/global/locked_down

If checked then uncheck - log off and log back on.

---

### Post by CLomax on 2008-09-28
You're correct, it was on. I managed to find it the option through UbuntuTweak. Everything is good now. Thank you.

---

