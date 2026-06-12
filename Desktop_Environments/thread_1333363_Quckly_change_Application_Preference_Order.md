---
title: "Quckly change Application Preference Order"
date: 2009-11-21
forum: Desktop Environments
---

### Post by PeEllAvaj on 2009-11-21
In KDE, the system chooses the program to launch an individual file according to the System Settings->File Associations->Application Preference Order.  This is a really nice way to do it, but my problem is, I want to update all 35 mimetypes at the same time to make VLC the top choice.

Is there any way to mass-update mimetypes' Application Preference Orders in Kubuntu?

Thanks!

---

### Post by Zorael on 2009-11-22
> The "InitialPreference" property determines which app is chosen to be the default (i.e., the one with the highest InitialPreference is the default). If the .desktop file for Amarok doesn't have that property, then just add a line that says "InitialPreference=9"

In the case of VLC, the file would be **/usr/share/applications/vlc.desktop**.

See [this](http://ubuntuforums.org/showthread.php?t=1326806) and [this](http://ubuntuforums.org/showthread.php?p=8365164) thread for general information about .desktop files. The mimeapps.list approach mentioned in them could do the trick too, but more work.

---

