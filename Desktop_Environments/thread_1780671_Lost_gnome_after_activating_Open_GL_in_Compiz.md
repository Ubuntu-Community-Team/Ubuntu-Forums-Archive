---
title: "Lost gnome after activating Open GL in Compiz"
date: 2011-06-12
forum: Desktop Environments
---

### Post by .broken. on 2011-06-12
Hello,

I ran the compiz --replace command and I was playing about with Compiz. I wanted to active that rotating desktop cube. The screen froze when I activated it and I ended up doing a hard reboot by pressing and holding the power button.

Now, when I log in, the gnome bar at the top has gone, the window 'decorations' have gone (no minimize, etc) and the new gnome launcher on the left of the screen has gone :(

Any advice on how to get thing back to the way they were?

Cheers,
James

---

### Post by .broken. on 2011-06-12
I've uninstalled Compiz, used metacity --replace and still no joy. Metacity is now back, though I need to run the command after each reboot.

I went to Ubuntu Classic at the login screen and then attempted a revert to Ubuntu - this failed to load the bar at the top and the launcher :(

Would really appreciate some help. I really liked the new launcher...

---

### Post by mcduck on 2011-06-12
THe default launcher and panels are Compiz plugins, so if you uninstalled Compiz you should start by reinstalling it.

After that it's just a question of enabling the UNity plugin in Compiz settings, and making sure no other plugin conflicts with it's keyboard shortcuts or anyhting like that.

Actually, a simple way to make sure the default Unity setup works correctly is opening a temrinal and running "unity --reset". That will make sure the Unity plugin is enabled and has sane settings...

---

