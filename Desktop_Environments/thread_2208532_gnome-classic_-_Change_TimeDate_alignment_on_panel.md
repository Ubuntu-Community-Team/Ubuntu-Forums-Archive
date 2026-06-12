---
title: "gnome-classic - Change Time/Date alignment on panel"
date: 2014-02-28
forum: Desktop Environments
---

### Post by joshua-mallory on 2014-02-28
Hello, I absolutly love Gnome 3. Currently I use the Gnome Classic Session (not gnome-fallback) for most of my work. My only gripe is that the right side of the top panel is very crowded. I would like to center the Time/Date on the panel, just like it is on the Gnome Shell Top Bar. Can someone tell me where to go to change this?

Thank You

---

### Post by joshua-mallory on 2014-02-28
SOLVED!
To change this I edited the /usr/share/gnome-shell/modes/classic.json from:

```

{
    "parentMode": "user",
    "stylesheetName": "gnome-classic.css",
    "overridesSchema": "org.gnome.shell.extensions.classic-overrides",
    "enabledExtensions": ["apps-menu@gnome-shell-extensions.gcampax.github.com","places-menu@gnome-shell-extensions.gcampax.github.com","alternate-tab@gnome-shell-extensions.gcampax.github.com","launch-new-instance@gnome-shell-extensions.gcampax.github.com","window-list@gnome-shell-extensions.gcampax.github.com"],
    "panel": { "left": ["activities", "appMenu"],
               "center": ["dateMenu"],
               "right": ["a11y", "keyboard", "volume", "bluetooth",
                         "network", "battery", "dateMenu", "userMenu"]
             }
}

```

To:

```

{
    "parentMode": "user",
    "stylesheetName": "gnome-classic.css",
    "overridesSchema": "org.gnome.shell.extensions.classic-overrides",
    "enabledExtensions": ["apps-menu@gnome-shell-extensions.gcampax.github.com","places-menu@gnome-shell-extensions.gcampax.github.com","alternate-tab@gnome-shell-extensions.gcampax.github.com","launch-new-instance@gnome-shell-extensions.gcampax.github.com","window-list@gnome-shell-extensions.gcampax.github.com"],
    "panel": { "left": ["activities", "appMenu"],
               "center": ["dateMenu"],
               "right": ["a11y", "keyboard", "volume", "bluetooth",
                         "network", "battery", "userMenu"]
             }
}

```

---

