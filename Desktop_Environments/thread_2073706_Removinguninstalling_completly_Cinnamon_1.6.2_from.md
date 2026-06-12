---
title: "Removing/uninstalling completly Cinnamon 1.6.2 from Ubuntu 12.04.1 LTS"
date: 2012-10-20
forum: Desktop Environments
---

### Post by Random20210831 on 2012-10-20
I am installed Cinnamon 1.6.2 (see list below) on Ubuntu 12.04.1. My chose is Unity and I now want to uninstall Cinnamon. How to do that?
Thanks in advance.

**Details:**
**Things to uninstall:**[FONT="Courier New"]
-nemo
-cinnamon
-cinnamon 2d
-cinnamon settings
-gnome classic
-gnome classic (no effects)
-all of gnome settings.[/FONT]

**UPDATE:** I am now solved problem.

---

### Post by MSemlali on 2012-10-24
Could share the way you solved it with us?

---

### Post by Random20210831 on 2012-10-24
> **MSemlali said:**
> Could share the way you solved it with us?

Yes. I am goed to Ubuntu Software Center and view repos. I am find "Cinnamon Stable" repo. Remove all packages from "Cinnamon Stable" repo. Remove PPA with command: ```
sudo add-apt-repository --remove ppa:gwendal-lebihan-dev/cinnamon-stable
``` Reboot computer.

---

### Post by mosaic2s on 2012-10-31
why did you uninstall it? 
I have been using it now for almost 2 weeks - and I am just thrilled to have a quicker interface.

in unity - 
the virtualbox requires 2 clicks to start. first the utility and then the virtual machine. earlier short cut was possible.
if i go back to gnome classic - the multiple window that are opened is not visible. HUD does not work. if you click the same icon again say - office, the display does not take you to previous window.
documents can not be accessed from one click.
HUD interferes with sw within virtualbox.

with cinnamon, i have best of both the worlds.
HUD works, keyboard short cuts for documents, gimp, calc, libreoffice, chrome have been setup. apart from the links to them readily visible in the bottom panel.
I am told the hot corner is quite like mac.

---

### Post by COMECON on 2012-10-31
> **mosaic2s said:**
> why did you uninstall it? 
I have been using it now for almost 2 weeks - and I am just thrilled to have a quicker interface.

in unity - 
the virtualbox requires 2 clicks to start. first the utility and then the virtual machine. earlier short cut was possible.
if i go back to gnome classic - the multiple window that are opened is not visible. HUD does not work. if you click the same icon again say - office, the display does not take you to previous window.
documents can not be accessed from one click.
HUD interferes with sw within virtualbox.

with cinnamon, i have best of both the worlds.
HUD works, keyboard short cuts for documents, gimp, calc, libreoffice, chrome have been setup. apart from the links to them readily visible in the bottom panel.
I am told the hot corner is quite like mac.

Cinnamon has a HUD? It automatically has it when it's installed on Ubuntu or it's something like a plugin/extension?

---

### Post by mosaic2s on 2012-10-31
yes. cinnamon has HUD that works with SUPER key.
it does not work as per unity interface. but it is sufficient and also how my mind works on system.

---

