---
title: "Add/Remove Programs button missing!?"
date: 2006-06-14
forum: Desktop Environments
---

### Post by oocce on 2006-06-14
Hi!
I'm just started to use Linux. Previously I have used Unix (not much)...
I installed Kubuntu and installed Gnome over Kubuntus Kde. After that I installed compiz ;)
Now I have problem with" Add/Remove Programs" button is missing... 
Any command wich would launch it?

---

### Post by BitTorrentBuddha on 2006-06-14
The command to launch it is ```
/usr/bin/gnome-app-install
``` but to replace it try looking under Applications -> Accessories -> Alacarte Menu Editor, then select applications up at the top, scroll down to the bottom of the right side and make sure that it's not just unchecked for some reason. If it's not there, click File -> New Separator, then click File -> New Entry. From there make one that looks like:> 
Name: Add/Remove...
Comment: Install and remove applications
Command: /usr/bin/gnome-app-install
Icon: (browse to /usr/share/icons/Human/24x24/apps/gnome-settings-default-applications.png)
That should give you the Add/Remove that comes default with a clean install

---

### Post by oocce on 2006-06-14
[QUOTE=BitTorrentBuddha]The command to launch it is ```
/usr/bin/gnome-app-install
``` but to replace it try looking under Applications -> Accessories -> Alacarte Menu Editor, then select applications up at the top, scroll down to the bottom of the right side and make sure that it's not just unchecked for some reason. If it's not there, click File -> New Separator, then click File -> New Entry. From there make one that looks like:
That should give you the Add/Remove that comes default with a clean install[/QUOTE]
Doesn't find gnome-app-install...
It must be something to do with the Gnome install over Kubuntu?

---

### Post by mjm115 on 2006-06-14
Try 

> 
sudo adept


---

### Post by oocce on 2006-06-14
[QUOTE=mjm115]Try[/QUOTE]
Yes, I can use this, but this is not **the** Add/remove thing?

---

### Post by BitTorrentBuddha on 2006-06-14
[QUOTE=oocce]Doesn't find gnome-app-install...
It must be something to do with the Gnome install over Kubuntu?[/QUOTE]
If all else fails, reinstall it ;) 
```
sudo aptitude install gnome-app-install
```

---

### Post by oocce on 2006-06-15
[QUOTE=BitTorrentBuddha]If all else fails, reinstall it ;) 
```
sudo aptitude install gnome-app-install
```[/QUOTE]
Thanks ;)

---

