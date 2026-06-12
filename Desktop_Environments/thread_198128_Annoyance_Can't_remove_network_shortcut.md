---
title: "Annoyance: Can't remove network shortcut"
date: 2006-06-16
forum: Desktop Environments
---

### Post by s3phiroth on 2006-06-16
Well this might seem rather simple, but i already tried eveything i could remember and it's becoming a huge annoyance.

I was experimenting with the creation of network shortcuts trough the Places > Connect to Server dialog, and i created two shortcuts for ssh servers, but now i can't seem to be able to remove them.

I right clicked the icons in the bookmarks on nautilus side panel and i can't select the remove option. I tried opening network:/// on nautilus, and i can't remove it either. I tried unmounting and then removing again, but no luck. I searched for it on gconf-editor and i found nothing, so i really ran out of options.

Why can't i remove them ? And how can i remove them ?

Thanks in advance.

---

### Post by InsaneBeast on 2006-06-16
hi, s3phiroth, (nice FFVII reference by the way)

You should be able to get rid of the network drives by right-clicking on the particular network folder thats currently on the desktop and clicking "unmount Volume" at the bottom of the pop-up panel.  I hope that helps.

---

### Post by s3phiroth on 2006-06-17
Like i said in my post, i tried that and nothing happened. But surprisingly enough, i left my computer on during the night and this morning when i came back...the shortcuts were gone. Weird. I tried creating another one, removing it, and this time it worked.

---

### Post by InsaneBeast on 2006-06-18
[QUOTE=s3phiroth]
I right clicked the icons in the bookmarks on nautilus side panel and i can't select the remove option. [/QUOTE]
Sorry for the confusion, I assumed that when you said you couldn't select the "remove" option you were referring to the "Move to Trash" option, which is disabled for network folder connections.  :D 

Its possible that the desktop didn't update immediately after you successfully severed the link.  In the future you might have success [refreshing the desktop]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_refresh_GNOME_desktop") or [restarting gnome]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_restart_GNOME_without_rebooting_computer").  Alternatively, waiting for dapper to fix itself also works.

---

### Post by djbon2112 on 2008-02-24
EDIT: Got a google link, nevermind.

---

