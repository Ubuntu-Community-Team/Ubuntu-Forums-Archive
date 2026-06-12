---
title: "Metacity as windows manager in KDE 4.5.1"
date: 2010-09-09
forum: Desktop Environments
---

### Post by piedro on 2010-09-09
Hi! 

In the systemsettings of KDE 4.5.1 (working on lucid lynx) I set the windows manager in "default applications" to "metacity". 
I hope to get the same design of applications like I did set up in gnome. 

This seems to work kind of, but metacity doesn't find the same icon sets it finds within gnome (same user!). 

So I have all my symbols and stuff on my desktop, but using some outdated standard symbols - probaly gnome default or something. 

How can I make the metacity appearance to lok for hte decorations and icons in the same place it does when using gnome? 

thx, 
piedro

---

### Post by regala on 2010-09-09
> **piedro said:**
> Hi! 

How can I make the metacity appearance to lok for hte decorations and icons in the same place it does when using gnome? 



all appearance and icons settings are "set up" by gnome-settings-daemon which does it for every application running in a gnome session. maybe trying and running gnome-settings-daemon would solve this, but bear in mind, this could not work and wouldn't be considered a bug at all by both teams :)

br, mathieu

---

### Post by piedro on 2010-09-09
thx for answering! 


so how to run the gnome-settings.daemon? 
when I run this in a terminal I get: 

"Failed to acquire org.gnome.SettingsDaemon" 

and i have no idea what it does mean. 

any hints? 

thx, 
piedro

---

### Post by regala on 2010-09-13
> **piedro said:**
> thx for answering! 


so how to run the gnome-settings.daemon? 
when I run this in a terminal I get: 

"Failed to acquire org.gnome.SettingsDaemon" 

and i have no idea what it does mean. 

any hints? 

thx, 
piedro

means something about dbus...
what if "dbus-launch gnome-settings-daemon" ?

br
ms

---

