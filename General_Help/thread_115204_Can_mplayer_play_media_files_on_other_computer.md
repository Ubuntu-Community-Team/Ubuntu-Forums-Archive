---
title: "Can mplayer play media files on other computer?"
date: 2006-01-10
forum: General Help
---

### Post by firingstone on 2006-01-10
Totem can well play media files on other computer in the same network by samba,but mplayer and realplayer cannot do the same thing, what they do is simply copy the whole media file on my disk first and then play it locally. 
How can I let mplayer play files with a path like smb://... as well. 
Is there a way that I do not need to mount all the share files first?
thx

---

### Post by lamego on 2006-01-10
Instead of using samba paths (like smb://) you shold just mount (equivalent to windows map drive) the directories on your system, like this you will be able to play them just as any local file.
A simple way to do this mount is using the menu, Places -> Connect To Server .

---

