---
title: "Opera Plugins Error."
date: 2005-09-22
forum: Desktop Environments
---

### Post by celluloid on 2005-09-22
Hey all,
I installed Opera from the official site. Open loading Opera I get this error message.

Opera encountered a problem during plug-in setup.
Plug-ins will not work properly.
Check your installation.

Could not start plug-in executable 'operamotifwrapper'.
/usr/lib/opera/plugins/operamotifwrapper-3
Please install Motif.

Plug-in path
(Path can be modified in Preferences dialog)

/usr/lib/opera/plugins


I have checked in /usr/lib/opera/plugins/ and there is no "operamotifwrapper-3" file/folder. I have looked for help on the debian and opera sites but no luck. Can anyone help me?

---

### Post by Xian on 2005-09-22
You need to install the libmotif or lesstif packages.

---

### Post by celluloid on 2005-09-22
[QUOTE=Xian]You need to install the libmotif or lesstif packages.[/QUOTE]
 Thanks heaps.
Works properly now. :)

---

