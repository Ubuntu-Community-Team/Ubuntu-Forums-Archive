---
title: "loading apps at desktop startup time"
date: 2005-07-04
forum: Desktop Environments
---

### Post by holr on 2005-07-04
Hi!

I have both kubuntu and ubuntu installed on the same computer. I like the klaptop and kdebluetooth from kde, but prefer the layout of the gnome (ubuntu) desktop. I can go into a terminal window and type the program names while in gnome to get them loaded (and they appear in the system tray area).

I would like to get them to run when I log into the gnome desktop manager - I have added the programs into the system->preferences->sessions (i think) and yes, they do load at desktop initialisation, but they do not appear in the system tray.... any ideas??

---

### Post by holr on 2005-07-05
can anyone help?

---

### Post by NeoChaosX on 2005-07-05
Do they appear in the tray when you start them manually?

---

### Post by holr on 2005-07-05
[QUOTE=NeoChaosX]Do they appear in the tray when you start them manually?[/QUOTE]
 hi! thanks for replying. When I start them manually, the icons do appear in the ubuntu system tray. Its when I try to get them to start as the desktop manager starts, they dont appear in there...

---

### Post by doclivingston on 2005-07-06
Some programs (but not all) have issues if they are loaded before gnome-panel is loaded (because the notification tray doesn't exist yet). Have you tried increating the vaue of "order" which should make them load later?

---

### Post by holr on 2005-07-06
[QUOTE=doclivingston]Some programs (but not all) have issues if they are loaded before gnome-panel is loaded (because the notification tray doesn't exist yet). Have you tried increating the vaue of "order" which should make them load later?[/QUOTE]
 ooh! ill give that a go and will get back to you. wonder what that option was for. It was at default "50". Can i find out where gnome-panel is?

---

