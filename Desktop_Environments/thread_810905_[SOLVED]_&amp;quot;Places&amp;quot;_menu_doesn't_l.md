---
title: "[SOLVED] &amp;quot;Places&amp;quot; menu doesn't launch Nautilus"
date: 2008-05-28
forum: Desktop Environments
---

### Post by Ebuntor on 2008-05-28
Hi everyone,

I've got a problem with my "Places" menu. The upper section, "Home Folder" "Desktop" and my bookmarks give the following error ```
Could not open location
There was an error launching the default action command associated with this location.
```However "Computer" and my other drives etc do work. I already tried editing the configuration files in /usr/share/applications/ but they all point to Nautilus. I also tried removing and reinstalling Nautilus and the Gnome panel.

Thanks in advance

---

### Post by Ebuntor on 2008-05-28
Seems I've fixed the problem. I remembered I installed PCMan File Manager earlier. 
I went to the dir /usr/local/share/applications and opened mimeinfo.cache

```
x-directory/normal=pcmanfm.desktop
inode/directory=pcmanfm.desktop
x-directory/gnome-default-handler=pcmanfm.desktop
```I changed all the pcmanfm entries to nautilus and everything is back to normal again. :)

```
x-directory/normal=nautilus.desktop
inode/directory=nautilus.desktop
x-directory/gnome-default-handler=nautilus.desktop
```

EDIT: I found out that after logging out the problem returned so I deleted the whole cache file and that did the trick.

---

