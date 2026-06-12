---
title: "Phantom startup programs when login in a session"
date: 2007-03-04
forum: Desktop Environments
---

### Post by gasull on 2007-03-04
Hello.

I have several programs opening when I start my Gnome session, but I don't see them in "startup programs" when I configure sessions in Preferences.  For example Firefox is opening every time I start Gnome.

It also seems that some programs aren't starting at login even if I do add them to Preferences -> Sessions -> Startup programs.  For example Ipodder isn't starting.

TIA.

---

### Post by eggdeng on 2007-03-04
Check what files you have in /home/your_username/.config/autostart. You should have one for each app you want to start and none for any you don't.

---

### Post by gasull on 2007-03-04
> **eggdeng said:**
> Check what files you have in /home/your_username/.config/autostart. You should have one for each app you want to start and none for any you don't.

No.  Firefox is starting with eveyry new sesion, and I don't have any Firefox-related file in ~/.config/autostart/

Thanks anyway.

---

