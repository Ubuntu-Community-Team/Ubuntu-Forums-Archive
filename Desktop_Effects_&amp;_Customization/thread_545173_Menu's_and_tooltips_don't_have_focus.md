---
title: "Menu's and tooltips don't have focus"
date: 2007-09-07
forum: Desktop Effects &amp; Customization
---

### Post by likwid on 2007-09-07
Hi

Somehow in gnome running compiz fusion my menu's no longer have focus, they're hidden behind any applications which might be running. The same is true of tool tips, they are hidden behind, for example, firefox.

Any ideas?

---

### Post by praet on 2007-09-07
Maybe check your panel settings in gconf-editor

/apps/panel/general/toplevel_id_list
top_panel_screen0

etc.

---

### Post by likwid on 2007-09-10
Thanks for answer.

This seems ok. The problem persists, but only sometimes. Sometimes on boot the problem occurs but then restarting X seems to fix it, probably restarting compiz is what is actually fixing it. 

If noone else is having this problem can someone advise how to reset all compiz settings, in order that i can check it's not my current configuration.

Cheers!

---

### Post by praet on 2007-09-10
In ccsm,  click on Preferences, near the profile buttons to import / export is "Reset to default".

---

