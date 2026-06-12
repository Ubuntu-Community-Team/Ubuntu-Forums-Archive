---
title: "gnome-main-menu (formerly SLAB) missing &quot;Applications&quot; tab"
date: 2007-10-22
forum: Desktop Environments
---

### Post by saintdev on 2007-10-22
I just upgraded to Gutsy the other day. Previously I was using gnome-main-menu instead of the Menu Bar. I like it a lot better, however after the upgrade the Applications tab is missing, as are all the entries in the System area (Help, Add/Remove Programs, Gnome Control Center, Lock Screen, Log Out).

I searched the forums, and the only post I could find is in the (now closed) Gutsy Development forum. [http://ubuntuforums.org/showthread.php?t=511922](http://ubuntuforums.org/showthread.php?t=511922)
I tried what was suggested there: manually launch application-browser (which is actually located at /usr/lib/gnome-main-menu/application-browser) and add a few programs to Favorites. The only problem is when I launch application-browser there is no option to add to favorites, like there should be. I tried editing/deleting the various .xbel files in ~/.config/gnome-main-menu/ and ~/.local/share/gnome-main-menu. I also tried playing with various settings in /desktop/gnome/applications/gnome-main-menu in gconf-editor, but nothing has changed.
I also created a new user, logged in for the first time and added gnome-main-menu to that user's panel. Still no Applications tab or anything in the System area.

This really makes having gnome-main-menu in the repo rather pointless as it is completely unusable without the Applications tab, or the System area. Is there any way to fix this, or am I stuck with the Menu Bar/Stock Gnome Menu?

---

### Post by Kalli on 2007-10-24
I'm having the exact same problem. It's really quite annoying! I use that thing a lot, I don't understand why it changed to become useless...

---

### Post by swildeboer on 2007-10-25
If you open the application browser using the path above /usr/ etc. etc. and then drag an icon to the 'Computer' button at the bottom and just drop it there (nothing opens), then the application menu will show up.

I've searched through the gconf-editor settings but I can't find much wrong there.

Hope this helps.

---

### Post by swildeboer on 2007-10-25
Actually it appears the system icons don't show up either. If you look in gconf-editor at desktop/gnome/main-menu/system-area you'll see there are no settings !?! Does anybody know how to fix this?

Regards...

---

### Post by Kalli on 2007-10-28
Well I'm stumped... it's like they decided to scrap the whole thing completely!

---

### Post by saintdev on 2007-10-28
> **Kalli said:**
> Well I'm stumped... it's like they decided to scrap the whole thing completely!

Actually it's more like they decided to build it and not bother to check if it worked or not. If you look through the xbel files there are lots of links to SuSE specific applications (YaST, etc) that they didn't even bother to change.

As I said it's completely useless having it in the repository in it's current state. The old version at least worked (even if it was really old).

Well, in case anyone is curious here are the various bugs that I've found on the subject:
[Bug # 149123 - gnome main menu missing favorite applications and system options](https://bugs.launchpad.net/ubuntu/+source/gnome-main-menu/+bug/149123)
[Bug # 148404 - search_command defaults to Beagle instead of Tracker](https://bugs.launchpad.net/ubuntu/+source/gnome-main-menu/+bug/148404) - This can be fixed in gconf-editor by changing the search command from "beagle-search SEARCH_STRING" to "tracker-search-tool SEARCH_STRING"

---

### Post by groggyboy on 2007-10-28
i know it doesn't help, but my SLAB menu works fine.

have you tried purging and reinstalling it?

---

### Post by juhanfg on 2007-10-30
All I needed is to fix this is to reinstall both gnome-main-menu and libslab0.

I hope this helps.

---

### Post by Kalli on 2007-10-31
> **juhanfg said:**
> All I needed is to fix this is to reinstall both gnome-main-menu and libslab0.

I hope this helps.

That did help, thanks. I'd already tried reinstalling gnome-main-menu and it did nothing...now I completely removed both and it's working fine :)

---

### Post by Kalli on 2007-11-01
> **saintdev said:**
> 
Well, in case anyone is curious here are the various bugs that I've found on the subject:
[Bug # 149123 - gnome main menu missing favorite applications and system options](https://bugs.launchpad.net/ubuntu/+source/gnome-main-menu/+bug/149123)
[Bug # 148404 - search_command defaults to Beagle instead of Tracker](https://bugs.launchpad.net/ubuntu/+source/gnome-main-menu/+bug/148404) - This can be fixed in gconf-editor by changing the search command from "beagle-search SEARCH_STRING" to "tracker-search-tool SEARCH_STRING"

I tried changing to tracker in gconf-editor but that didn't do anything... any ideas?

---

### Post by Kalli on 2007-11-12
Has anybody got a Tracker searchbar working in their menu (Like the one that comes when you install Beagle)?  Is that even possible?

---

