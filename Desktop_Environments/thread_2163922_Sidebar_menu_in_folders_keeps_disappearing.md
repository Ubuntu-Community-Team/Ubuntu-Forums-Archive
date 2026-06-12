---
title: "Sidebar menu in folders keeps disappearing"
date: 2013-07-20
forum: Desktop Environments
---

### Post by Hasse on 2013-07-20
Hi!

The sidebar menu in my folders (see attached picture) keeps disappearing. If I press F9 two(!) times it comes back, but if I close the folder and open it again, it's gone.

Any smart people out there who knows what to to?

Thanks in advance!

---

### Post by SantaFe on 2013-07-20
Not using Unity or Nautilus, but I think you click on the gear icon in the upper right corner & there should be a View option, where you can click on Show Sidebar.

Or you can follow the instructions [Here]("http://amahanty.wordpress.com/2012/08/11/enable-nautilus-toolbar-statusbar-and-sidebar-with-tree-view/")

---

### Post by rohdin.hansgmail.com on 2013-08-01
The "Show Sidebar"-option is already checked. If I un-check it and check it again, the sidebar appears. But, when I close the folder and open it again, the sidebar is gone. This option is the same thing as pressing F9 i suppose. I can't follow the instructions in the link either because "nautilus" is not available in my "gconf-editor"-list..

What do you think?

---

### Post by koma77 on 2013-09-30
> **Hasse said:**
> Hi!

The sidebar menu in my folders (see attached picture) keeps disappearing. If I press F9 two(!) times it comes back, but if I close the folder and open it again, it's gone.

Any smart people out there who knows what to to?

Thanks in advance!


I have the exact same problem. Did you ever manage to solve it?

Or does anyone else know why I have to de-select and then re-select "Show sidebar" in order for it to show up?

---

### Post by mc4man on 2013-09-30
In dconf-editor as in screen
or in terminal
```
gsettings set org.gnome.nautilus.window-state start-with-sidebar true

```

---

