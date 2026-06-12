---
title: "problem with systray module in cairo-dock"
date: 2008-02-17
forum: Desktop Effects &amp; Customization
---

### Post by brazilla ray on 2008-02-17
I've been having trouble with the systray module in cairo-dock (v1.5.0.1).  When I add the module to the dock, the systray icon appears, but nothing else, and when I click on it, cairo-dock crashes.  When run from the terminal, I get this before it crashes:
```

cairo-dock: symbol lookup error: /usr/share/cairo-dock/plug-in/libcd-systray.so: undefined symbol: cd_desklet_new

```
I also get:
```

cp: cannot stat `/usr/share/cairo-dock/plug-in/gnome-integration/none': No such file or directory
Attention : couldn't copy /usr/share/cairo-dock/plug-in/gnome-integration/none in /home/:(/.cairo-dock/current_theme/plug-ins/gnome-integration; check permissions and file's existence

```
when cairo-dock opens, which seems important.
Also, maybe related, maybe not:
```

Attention : Attention : this module ('/usr/share/cairo-dock/plug-in/libcd-powermanager.so') was compiled with Cairo-Dock v1.5.0, but Cairo-Dock is in v1.5.0.1
  It will be ignored
Attention : Attention : this module ('/usr/share/cairo-dock/plug-in/libcd-terminal.so') was compiled with Cairo-Dock v1.5.1-090208, but Cairo-Dock is in v1.5.0.1
  It will be ignored

```
I have tried installing it every way I can think of, from source, debs, repositories; all the same.  Currently I have it installed by updating an older version.  The older version seemed to work fine, but doesn't have the systray module.
Has anyone else had this problem, or know of any way to fix it?
Thanks!

---

