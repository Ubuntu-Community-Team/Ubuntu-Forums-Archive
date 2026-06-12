---
title: "how do i add kmail to menu?"
date: 2006-02-11
forum: Desktop Environments
---

### Post by fuscia on 2006-02-11
i'm trying to use kmenuedit to add kmail to the menu (and eventually to the panel). when it asked for a path, that's when the linuxdeer appeared.

[IMG]http://img.photobucket.com/albums/v342/unknownentity/linuxdeer2.jpg[/IMG]

---

### Post by Neo Ex on 2006-02-11
Copy the /usr/share/applications/kde/kmail.desktop file in ~/.local/share/applications . Then, rename it kde-kmail.desktop. Open it with a text editor and delete the line saying 'NoDisplay=true' (it's the last one).
Then, log out and re-login, or run from a terminal 'kbuildsycoca' (or also wait for a while), and KMail will be shown in you K menu.

---

### Post by fuscia on 2006-02-11
thank you.

---

