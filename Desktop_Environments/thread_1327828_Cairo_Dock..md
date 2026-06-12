---
title: "Cairo Dock."
date: 2009-11-15
forum: Desktop Environments
---

### Post by Roasted on 2009-11-15
I decided to start fresh since I had so many weird settings in my Cairo Dock to just nuke it and start from ground up, but I had a hard time getting it installed. If I installed from the repos, I didn't get ANY menu items under system tools like I did before. Then I remembered I had saved the 2 debs from cairo dock, which was the application itself + the plugin package. Installed them and now I have ONE launch icon for no open GL, but I dont have the open GL option like I used to.

What happened? How can I nuke everything from cairo dock and start from ground up as if I never installed it?

---

### Post by fabounet on 2009-11-16
well just install it by following the few steps on the wiki (you should maybe remove it before to avoid conflicts)
[http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en")
bacically, you just add the Cairo-Dock's repository, and then install it like any other application.

but if you really have some troubles with the current theme, you can just restart with a fresh theme by deleting (or renaming) the folder ~/.config/cairo-dock/current_theme, and restarting the dock.

---

