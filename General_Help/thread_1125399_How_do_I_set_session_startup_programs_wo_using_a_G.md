---
title: "How do I set session startup programs w/o using a GUI tool?"
date: 2009-04-14
forum: General Help
---

### Post by Keatonguy on 2009-04-14
Hi again, folks.

I'm administrating a high-use LTSP server, and I'm trying to cut back on ram usage by disabling some of the processes that start automatically when users log in to GNOME, but I only know how to configure a few basic things for the individual user via the 'Session' gui.

So, where are the settings this program edits stored? And is there a way I can adjust these settings system-wide?

Thanks in advance.

---

### Post by CatKiller on 2009-04-14
This isn't necessarily a full solution for you, but I believe these are stored as .desktop files in ~/.config/autostart. The .desktop format is pretty straightforward; you can pick it up from pretty much any launcher, since these are all .desktop files. The key thing for these files, though, I think, is that they contain the line ```
X-GNOME-Autostart-enabled=true
``` So if there was something that you wanted to add to the startup for all users, you would put an appropriate file in each of those users' Home folders.

If you also wanted it to be applied to all new users automatically too, I understand that /etc/skel is the template for a new user's Home folder. So putting .desktop entries in /etc/skel/.config/autostart should give them some autostart entries.

Actually, I've just had a quick search, and it looks like Ubuntu's default autostart entries are in /etc/xdg/autostart. So changing the Autostart-enabled key to false for the appropriate entries in there should disable those from autostarting for new users. You'd probably still have to manually change any existing users' configurations, though.

---

