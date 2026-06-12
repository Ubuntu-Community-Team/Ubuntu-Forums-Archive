---
title: "log out menu options missing"
date: 2005-04-14
forum: Desktop Environments
---

### Post by burlap on 2005-04-14
I have upgraded from Warty to Hoary and there is no option to hibernate in the log out menu. (I have seen it in Hoary installed from scratch). 

How to enable it: do I have to reconfigure some packages? Reinstall? 

BTW: Hibernate works for me (with minor adjustments), so this option might be useful...

---

### Post by müller on 2005-06-11
you enable the hibernate option by uncomenting the line in
/etc/default/acpi-support

---

### Post by burlap on 2005-06-12
Maybe I wasn't clear: I have hibernate enabled, it works (started manually from CLI). "Hibernate" option is missing in gnome panel log out menu (I have only: log out, shut down and restart)

---

