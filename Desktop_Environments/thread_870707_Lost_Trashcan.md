---
title: "Lost Trashcan"
date: 2008-07-26
forum: Desktop Environments
---

### Post by Y^2om&amp;#7sgP on 2008-07-26
Sorry if this has been asked a million time or if I'm asking in the wrong forum, but am still very new to Linux.

I've managed to remove my trashcan from the taskbar and now each time I try to add it back I get the message

The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet".

Can anyone tell me how to get this back please?

of course I could just re-install from scratch, but this way I may even learn something more about Linux :)

Thanks

---

### Post by Tim Sharitt on 2008-07-26
In a terminal
```
sudo apt-get install --reinstall gnome-applets
```

---

### Post by ajgreeny on 2008-07-26
If it is just your trashcan that has gone missing, try right clicking in the panel and chose "Add to Panel."  Then simply add the Deleted Items icon again.  Hopefully all will now be well, with your trashcan back where you want it.

There are a lot of other applets available in this way, so have a look around and you may find other useful items.

---

