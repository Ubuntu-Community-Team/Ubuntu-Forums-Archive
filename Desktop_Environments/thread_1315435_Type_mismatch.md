---
title: "Type mismatch:"
date: 2009-11-05
forum: Desktop Environments
---

### Post by jbtphotos on 2009-11-05
I'm running 9.10 and have started to receive the following error once I've completed booting:

Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name


Any ideas?


Jeff

---

### Post by frederik.heremans on 2009-11-05
Can it be that you configured a custom name for your "Computer" icon on the desktop, or maybe using a name that only contains "numeric" characters? 
Use gconf-editor to inspect value of /schemas/apps/nautilus/desktop/computer_icon_name

check out [http://www.gnome.org/~bmsmith/gconf-docs/C/nautilus.html]("http://www.gnome.org/%7Ebmsmith/gconf-docs/C/nautilus.html")

---

### Post by frederik.heremans on 2009-11-06
Any success?

---

