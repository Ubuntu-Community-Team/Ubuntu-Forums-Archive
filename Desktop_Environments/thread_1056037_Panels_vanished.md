---
title: "Panels vanished"
date: 2009-01-31
forum: Desktop Environments
---

### Post by Jaded Misanthrope on 2009-01-31
I booted up Ubuntu a few minutes ago and found that my panels have vanished with no explanation. A search suggested that I could rectify this by going to alt-f2 and typing 'killall gnome-panel' but alt-f2 doesn't cause any window to open.

I can still open the terminal using a keyboard shortcut I set up, but I can't connect to the Internet -- I need the panel to select the network! -- so I'm typing this on a different computer. Are there any terminal commands that may have the Gnome panels reappear (killall gnome-panel did nothing).

I have not installed Compiz or altered the desktop environment, if it's significant.

---

### Post by gettinoriginal on 2009-01-31
In terminal try:
```
sudo apt-get update
```
```
sudo apt-get install --reinstall gnome-panel
```

---

