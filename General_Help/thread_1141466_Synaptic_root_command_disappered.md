---
title: "Synaptic root command disappered"
date: 2009-04-28
forum: General Help
---

### Post by cookie132 on 2009-04-28
I need my Synaptic to launch competely from the menu. Right now I can only launch it from the command line using either gksu or sudo. If I do launch from the menu I get a popup that asks for my password and it has Command: , but no command. When it was working it had Command: gksu /usr/sbin/synaptic . How do I fix it? Can I edit a text file somewhere to put the command back?

---

### Post by michy99 on 2009-04-28
Do a right click on the menu bar and choose "Edit Menus". Find the entry for Synaptic Package Manager. Right click on it and choose "Properties". Enter ```
gksu /usr/sbin/synaptic
``` in command.

---

### Post by abn91c on 2009-04-28
Kubuntu uses [COLOR="Blue"]Adept manager[/COLOR] by default, not synaptic

---

### Post by cookie132 on 2009-04-28
It Worked! i installed synaptic on kubuntu. I do not like adept package manager. I probably have the wrong prefix

---

