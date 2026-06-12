---
title: "Nautilus in Plasma Environment"
date: 2013-04-10
forum: Desktop Environments
---

### Post by irancplusplus on 2013-04-10
I use Plasma Invirenment in Ubuntu 12.10. However I use Nautilus to view files. I have two problems with Nautilus:


1) It sometimes hides the Plasma Desktop. Because first run of Nautilus, opens a Desktop a default Folder View. (it's similar to Windows Explorer)


2) In Dolphin when an item is double clicked, an animation beside mouse pointer shows it will be opened soon. But in Nautilus there's not any animation. So sometimes I'm not sure if the double click is accepted.


Is there any option to solve these problem?

---

### Post by zombifier25 on 2013-04-10
Well 2) works for me (in Unity), so I can't really help. But for 1, it's because Nautilus, besides from being a file manager, also controls your desktop and will happily take over it when started.
To disable this feature, install the package "gnome-tweak-tool". Type this into the terminal:
```
sudo apt-get install gnome-tweak-tool --no-install-recommends
```
(I added the --no-install-recommends flag since apparently it pulls in some unneeded GNOME packages)
Then launch it, go to the "Desktop" section and disable "Have file manager handle the desktop".

---

### Post by ajgreeny on 2013-04-10
Try opening nautilus with the command ```
nautilus --no-desktop
``` which should allow nautilus to run but not try to write the user's desktop display.

I don't know KDE well enough to comment on the way to show a startup-notification, so will leave that to others.

---

### Post by irancplusplus on 2013-04-10
thanks.

> [COLOR=#000000]2) works for me (in Unity)[/COLOR]
it doesn't work for me even in unity. there may be some option which enables/disables it.

---

