---
title: "[SOLVED] Number of virtual desktops fixed at 2"
date: 2008-11-04
forum: Desktop Environments
---

### Post by avatar1983 on 2008-11-04
Hi all, long time (k)ubuntu user, first time poster here!

I have been experiencing a really quite odd issue with kubuntu intrepid. Regardless of what number of virtual desktops I set in the System Settings -> Desktop -> Multiple Desktops menu, I always get only 2 virtual desktops. I have even trawled the .kde/share/config files for settings related to this option, and they seem to be located in kwinrc. The number of desktops there is set correctly to Number=4 in the [Desktops] section, but I still only get 2 virtual desktops.

My google-ing has turned up nothing on this issue. Anyone got any ideas?
Thanks in advance for any help!

---

### Post by grotto on 2008-11-04
Are you using Compiz by any chance?

---

### Post by avatar1983 on 2008-11-04
No, I'm using Kwin, with the built-in effects. Incidentally, it makes no difference if I turn those on or off.

Then again. it is an upgraded hardy install, where I did use compiz with KDE 3.5. Not sure whether that can make any difference.

---

### Post by grotto on 2008-11-04
I thought of compiz because it can control the number of desktops as well. 

If you're using KDE4, I think kwinrc is in .kde4 now. ~.kde4/share/config/kwinrc

Might be able to copy over the old KDE3 settings.

---

### Post by avatar1983 on 2008-11-04
I know compiz can control the number of desktops (it's what I used in hardy and KDE3.5). Actually, in intrepid kubuntu the KDE 4 settings now reside in ~/.kde, not ~/.kde4 as it is now the only supported version of KDE. ~/.kde4 is now not used at all. I'll try to see if there are any leftover compiz settings I can purge. Maybe that will help.

Thanks for your interest so far, by the way. I appreciate your help.

---

### Post by grotto on 2008-11-04
Ahh, you're right. Thanks for the correction. 

[Some one else]("http://kubuntuforums.net/forums/index.php?topic=3098736.0") had the same issue on another forum. But didn't have a fix. I can't find anything on [https://bugs.kde.org]("https://bugs.kde.org") either. 

I'm not being very helpful, heh. :sad:

---

### Post by avatar1983 on 2008-11-04
Fixed!

I fixed it by opening up ccsm (compiz config settings manager) and changing the number of desktops there. Which is strange as I no longer use compiz.

But it seems that Kwin uses it's own packaged version of compiz to create display effects, and if there is left over stand alone compiz configuration it gets confused. That is kind of irritating. Well, at least it is fixed now.

---

### Post by perspectoff on 2008-12-06
> **avatar1983 said:**
> Fixed!

I fixed it by opening up ccsm (compiz config settings manager) and changing the number of desktops there. Which is strange as I no longer use compiz.

But it seems that Kwin uses it's own packaged version of compiz to create display effects, and if there is left over stand alone compiz configuration it gets confused. That is kind of irritating. Well, at least it is fixed now.

I'm using Compiz on Kubuntu Intrepid Ibex. I can't find where to set the number of desktops in the Compiz Settings Manager. Where is it?

---

### Post by Cypher on 2009-01-14
In the Compiz Settings Manager, General Options, Desktop Size tab. Increase the Horizontal Virtual Size to get more workspaces..

---

