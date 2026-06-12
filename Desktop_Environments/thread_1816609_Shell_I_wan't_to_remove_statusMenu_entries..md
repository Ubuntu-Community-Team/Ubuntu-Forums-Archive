---
title: "Shell: I wan't to remove statusMenu entries."
date: 2011-08-02
forum: Desktop Environments
---

### Post by hhh on 2011-08-02
I'm trying to remove items from gnome-shell's status menu (Available, Busy, Account, etc...). I had them successfully removed but didn't pay enough attention to how I did it as I ended up having other major issues that required a new install, and now I can't figure it out.

I could have sworn that in /usr/share/gnome-shell/js/ui/statusMenu.js I removed, for example, lines 197-199, but that's not working for me.

Any help would be great, thanks.

---

### Post by wheelerthomas on 2011-12-06
I know this entry is old but status menu has been changed to usermenu.js and you should create an extension to do this instead of editing the core UI files.

---

