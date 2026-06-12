---
title: "Where did my titlebars go?"
date: 2005-06-27
forum: Desktop Environments
---

### Post by chaumurky on 2005-06-27
Suddenly all my application windows are missing their titlebars so I can't move or close them (unless there's an option in the menu). The windows also don't appear in the panel. When I try to access System>Preferences>Windows I get an error "Cannot start the preferences aplication for your window manager. Window manager "unknown" has not registered a configuration tool" Does that message give anyone an idea what's up? I'm using gdm but I'm not fully clued up about how it works under the hood with Gnome. I haven't fooled with anything  O:) except ~/.vnc/xstartup for my vnc sessions (just added exec gnome-session ).

---

### Post by chaumurky on 2005-06-27
Just a quick addition, the problem doesn't exist when I log in as root. Perhaps there is a way to reset gnome to it's default settings - that may fix the problem?

---

### Post by derrick1985 on 2005-06-27
Right click on a panel---New Panel
Right click on your new panel, add to panel
Select from list, Window List

---

### Post by chaumurky on 2005-06-27
[QUOTE=derrick1985]Right click on a panel---New Panel
Right click on your new panel, add to panel
Select from list, Window List[/QUOTE]
 Sorry, I now have 2 window lists in the panel that have no items in them, and my windows still have nop title bars. Any other ideas?

---

### Post by chaumurky on 2005-06-27
It appears to have been as simple as deleting the "Default" session. I would have liked to have figured out what would cause such a problem but I'll be content with this.  :)

---

