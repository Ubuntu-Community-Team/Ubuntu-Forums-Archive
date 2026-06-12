---
title: "Wine menu disappeared for good?"
date: 2011-03-16
forum: Desktop Environments
---

### Post by GNUbee40 on 2011-03-16
Hi there!

I de- and reinstalled Wine a couple of times after having some bad luck witch a Windows app which messed things up a little. 
I wondered why the Wine entries in the main menu would not dissapear upon deinstallation and deleted them myself using alacarte.
Now, when i reinstall Wine the main menu entries are no longer created. When i reinstall my windows program the same.
Does alacarte have something to do with this? How can i reenable automatic creation of main menus?

---

### Post by MSPdwalt on 2011-03-16
Post #3

[http://ubuntuforums.org/showthread.php?t=1030787](http://ubuntuforums.org/showthread.php?t=1030787)

[IMG]http://img854.imageshack.us/img854/8478/selection040.png[/IMG]

---

### Post by GNUbee40 on 2011-03-16
Well!

I found that whenever you delete an folder in alacarte (the program used by System/Settings/Main Menu) this is made permanent by placing an application.menu file under homefolder/.config/menus/ in which Wine folders are permanently marked as deleted. This file seems to be merged with the etc/xdg/menus/application.menu file. The latter seems to be the main file determining how the main menu looks like.
Using the "take back changes" function in alacarte I could restore the menus, but this included old ones from already deinstalled programs under Wine.
It seems then that one cannot delete these old entries in alacarte without compromising the creation of new entries in the wine menu. 
Instead, they could hasslefree be removed by deleting the appropiate .menu file in homefolder/.config/menus/applications-merged.
All in all a bit tedious. But glad i found a solution before midnight.:)

---

### Post by GNUbee40 on 2011-03-16
Well - seems I did not use the right search terms. anyhow thanks. Still wondering when the gnome menu becomes foolproof.

---

### Post by MSPdwalt on 2011-03-16
Not sure, but you're particular issue seems to be more related to the wine uninstall process than the gnome menu (which I googled around for when I had the issue and found nothing lol)

Don't forget to mark your thread as solved ;)

---

