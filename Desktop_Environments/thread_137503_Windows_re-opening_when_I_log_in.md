---
title: "Windows re-opening when I log in"
date: 2006-02-28
forum: Desktop Environments
---

### Post by melat0nin on 2006-02-28
Hi guys,

Some windows keep re-opening when I log into Ubuntu, and they're not Nautilus windows (which might be expected) - it's Terminal, gconf-editor and nautilus.  It's really irritating.

How do I stop this happening?

-m

---

### Post by melat0nin on 2006-02-28
I've managed it (I think) by closing everything then saving the session settings and logging out then back in.  I had to manually kill the gconf-2 process in the System Monitor to prevent the Configuration Manager re-appearing, though.

---

### Post by codejunkie on 2006-02-28
[QUOTE=melat0nin]Hi guys,

Some windows keep re-opening when I log into Ubuntu, and they're not Nautilus windows (which might be expected) - it's Terminal, gconf-editor and nautilus.  It's really irritating.

How do I stop this happening?

-m[/QUOTE]
close all open windows and applications you don't want autostarting then press Alt+F2 and enter ```
gnome-session-save
```

---

