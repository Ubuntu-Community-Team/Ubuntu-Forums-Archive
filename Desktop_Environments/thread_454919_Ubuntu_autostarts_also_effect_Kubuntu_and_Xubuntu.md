---
title: "Ubuntu autostarts also effect Kubuntu and Xubuntu?"
date: 2007-05-26
forum: Desktop Environments
---

### Post by wilberfan on 2007-05-26
I'm experimenting with the Big Three desktop environments, and I've got a question about apps that autostart...

I installed Ubuntu first--and it seems that all (most?) of my autostarted gnome apps seems to start up in kde and xfce too?

Beryl seems to autostart in all three--but there is nothing in ~/wilberfan/.kde/Autostart.   Gkrellm starts in all three, also...but I've done nothing specific in kde or xfce to accomplish that...

Likewise, tilda only seems to autostart in gnome--not kde or xfce...

It seems like the gnome settings are having an effect on the other two (?)--is there a way to tweak each environment so only the things I specify autostart??

---

### Post by afoglia on 2007-06-05
In XFCE, there's an "Autostarted Applications" item in the Settings menu.  Check there first.  Also, there's a "Sessions and Startup" program in there.  Under Advanced, try unclicking "Launch Gnome services on startup."

---

