---
title: "gnome-shell problem"
date: 2011-10-24
forum: Desktop Environments
---

### Post by jakelong00 on 2011-10-24
so i installed ubuntu 11.10 and was not liking the unity interface and installed gnome-shell.
i was adding some extensions to it and when restarted it saw a white bar with options like file,view,help n couple more.
i removed the extension packages and now i have this.
how to remove that white bar below the taskbar?

---

### Post by crdlb on 2011-10-24
When nautilus is managing the desktop (which is optional; desktop icons don't fit in very well with GNOME Shell), Ubuntu's global menu stuff leaves a menubar under the top panel. You're seeing it because you're using a Shell theme with transparency. The two current workarounds are to disable desktop icons in gnome-tweak-tool or to uninstall appmenu-gtk3 and restart nautilus (this affects Unity as well).

---

### Post by jakelong00 on 2011-10-25
so i did what u told.
when i disabled desktop icons it worked fine for the first time but after logging out and again logging in the white bar was still there.
same happened when i removed the appmenu-gtk3.
now its almost unusable in normal mode

---

