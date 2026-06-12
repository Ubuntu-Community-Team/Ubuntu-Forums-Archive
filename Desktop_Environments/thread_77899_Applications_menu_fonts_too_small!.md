---
title: "Applications menu fonts too small!?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Hitman1 on 2005-10-17
After I upgraded ubuntu from 5.04 to 5.10, I noticed that some applications menu fonts became too small like evolution and firefox. How can I correct this? I tried to change the KDE fonts in the control centre but none affected these programs.

---

### Post by GeneralZod on 2005-10-17
These are both GTK apps.  Try installing gtk2-engines-gtk-qt

```

sudo apt-get install gtk2-engines-gtk-qt

```

enable it in the KDE control centre (it will be under Appearances->Gtk Styles and Fonts) and restart your two apps.

---

### Post by Iuliux on 2005-10-17
[QUOTE=GeneralZod]enable it in the KDE control centre (it will be under Appearances->Gtk Styles and Fonts) and restart your two apps.[/QUOTE]

becouse of the system setings you will have to run control centre with katapult (alt+space) and write control center (now press enter).

---

### Post by Freddy on 2005-10-17
> becouse of the system setings you will have to run control centre with katapult (alt+space) and write control center (now press enter).
Hmm isn't it kcontrol you mean?   /// Freddan

---

