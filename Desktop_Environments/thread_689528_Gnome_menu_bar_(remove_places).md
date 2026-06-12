---
title: "Gnome menu bar (remove places)"
date: 2008-02-06
forum: Desktop Environments
---

### Post by PurposeOfReason on 2008-02-06
Is it possible to configure the main menu applet so instead of having applications - places - system, it just has Applications - System and then put the places menu under system?

---

### Post by bwhite82 on 2008-02-06
I'm not sure, but have you checked out gconf-editor? It has a host of configuration options.

---

### Post by PurposeOfReason on 2008-02-09
Sadly not an option, but I might stand a shot if I can find the source code. However, I've spend the last 20 minutes looking and all because of that mac menu thread, half the results are that and I can't find it. Any places I should look?

---

### Post by tcommbee on 2008-02-09
things like menues are defined in special config files. you could try to google "xdg menu spec"

---

### Post by PurposeOfReason on 2008-02-09
The thing is I'm not editing the menu, but the applet.

---

### Post by KofolaMaster on 2008-03-03
just for reference - disabling the "places + system" menu item is done through "gconf-editor" -> apps -> panel -> objects ... -> uncheck "use_menu_path"
source:
[http://sudan.ubuntuforums.com/showthread.php?t=707997](http://sudan.ubuntuforums.com/showthread.php?t=707997)

---

### Post by asaz989 on 2008-05-06
Thanks for the input, KofolaMaster.

Still, not really the question (I'm wanting to do the same thing). Does anyone know how to get rid of (or at least customize, beyond just changing the contents of "Bookmarks") the Places menu on the menubar?

---

