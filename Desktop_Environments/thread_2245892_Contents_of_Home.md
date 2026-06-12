---
title: "Contents of Home"
date: 2014-09-26
forum: Desktop Environments
---

### Post by anon_private on 2014-09-26
Recently, I made a mistake a started to copy folders from root into home (kubuntu ver 14).

I have deleted most of the copied folders in home, but have forgotten the default structure.

At present, I have in home:

Desktop, Documents, Downloads, media, Music, Pictures, Public, Templates, tmp, Videos.

I believe that media and tmp should be removed.

Can someone give me a check.

Thanks

---

### Post by deadflowr on 2014-09-26
Well, yes, those two aren't normal.
I think you have might notice that the default folders in home are all capitalized.

so, yes, outside of those two, you have the defaults listed, as far as I can see.

---

### Post by Rog131 on 2014-09-28
**Default User Directories**

The default user directories are coming from the xdg-user-dirs specification: [http://www.freedesktop.org/wiki/Software/xdg-user-dirs/](http://www.freedesktop.org/wiki/Software/xdg-user-dirs/)

man page on line: [http://manpages.ubuntu.com/manpages/trusty/man1/xdg-user-dirs-update.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/xdg-user-dirs-update.1.html)

The default: 

> cat /etc/xdg/user-dirs.defaults
...
DESKTOP=Desktop
DOWNLOAD=Downloads
TEMPLATES=Templates
PUBLICSHARE=Public
DOCUMENTS=Documents
MUSIC=Music
PICTURES=Pictures
VIDEOS=Videos
...

The names and the directory paths are editable - KDE tool: KDE System Settings > Account Details > Paths. This is editing the ~/.config/user-dirs.dirs

More - Ubuntu - permanently remove ~/Videos and ~/Public: [http://superuser.com/questions/223918/ubuntu-permanently-remove-videos-and-public](http://superuser.com/questions/223918/ubuntu-permanently-remove-videos-and-public)

---

