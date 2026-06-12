---
title: "Unity: zombie apps don't launch anything"
date: 2011-08-07
forum: Desktop Environments
---

### Post by parsim on 2011-08-07
When I open my Unity dock and type "banshee", I get two results under Applications, both labeled "Banshee Media Player" with the exact same icon. If I click the first one, Banshee is launched. If I click the second, nothing is launched.

Not a big deal, but I'm wondering why this is, and how I can remove the useless zombie Banshee.

---

### Post by mc4man on 2011-08-07
Shouldn't be happening - there are 3 banshee .desktops in /usr/share/applications, 2 of them should have a line near the top of the .desktop
```
NoDisplay=true
```
That is supposed to prevent it from being seen in dash and most context menus

You could try purging banshee, then re-installing along w/ whatever else gets removed (and maybe a logout/in

Or ck. the .desktops, not sure which of the 2 is showing that shouldn't so open them both and ck.
Screens shows the correct line in both, line 3 - if missing just add
In terminal
 ```
gksudo gedit /usr/share/applications/banshee-*
```

---

### Post by parsim on 2011-08-07
Aha! Thank you! You gave me the idea to go hunting for .desktop files, which revealed this:

```
$ locate banshee | grep desktop
~/.local/share/applications/banshee-1-audiocd.desktop
~/.local/share/applications/banshee-1-media-player.desktop
~/.local/share/applications/banshee-1.desktop
/usr/share/app-install/desktop/banshee.desktop
/usr/share/applications/banshee-audiocd.desktop
/usr/share/applications/banshee-media-player.desktop
/usr/share/applications/banshee.desktop
```

The ones in ~/.local had "banshee-1" in their Exec lines, instead of "banshee" (like the ones in /usr/share/applications/). I deleted them and the problem is solved!

For some reason, my Banshee uses "banshee-1" for its config files (e.g. I have a ~/.gconf/apps/banshee-1/ directory, a ~/.config/banshee-1/ directory, and a ~/.cache/banshee-1/ directory, but no corresponding ~/.config/banshee/, etc). But this isn't causing any problems that I can see.

Thank you so much!

---

### Post by mc4man on 2011-08-07
Should of thought of that, most .desktops that don't have NoDisplay=true in any of the common applications directories will show in dash

As far as banshee-1 - the name was changed pre natty release to banshee but it still writes config changes to gconf as banshee-1 ( a bit of an over-site
Not sure why you had those .desktops in ~/, maybe you did an upgrade vs. fresh install

---

