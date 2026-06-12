---
title: "Gnome desktop broken"
date: 2008-12-05
forum: General Help
---

### Post by grkuntzmd on 2008-12-05
I am running Ubuntu 8.10. I normally use gnome as my window manager, but today I (stupidly:)) logged in under a KDE session to try it. After logging out and back in (to gnome), my desktop was empty (no icons). Mouse clicks on the desktop are ignored. The menus still work and I can start all of my apps normally (and they work fine), but no desktop icons.

I was going to remove ~/.metacity, but it does not exist.

Any ideas?

---

### Post by Forlong on 2008-12-05
Does it come back when running ```
nautilus
```

If not, what's the output of
```
gconftool-2 -g /apps/nautilus/preferences/show_desktop
```

---

### Post by grkuntzmd on 2008-12-05
That'll teach you to keep your cotton-pickin' hands to yourself!

I found a post a couple of days ago showing how to change the default file manager from nautilus to something else (in my case, dolphin), by editing the /usr/share/applications/nautilus-folder-handler.desktop. Last night I decided to see what would happen if I changed some of the other nautilus*.desktop files.

I found out the hard way.

Your suggestion to try the command "nautilus" was the key.

Thanks.

---

