---
title: "Gedit loads wrong icon theme"
date: 2015-06-20
forum: Desktop Environments
---

### Post by steve205 on 2015-06-20
Hi all,

I'm a long-time Linux user (about 12 years now), but will never pretend to be a master of it. I suspect my question here is rather simple, but I'm hoping the forum here can help all the same.

I just installed Ubuntu 14.04 LTS (should be 14.04.2 LTS, I think) on Thursday after having 12.10 run for a year without support.  I also installed a host of desktop environments I've never used before (namely XFCE and Cinnamon), as well as a lot of different icons and themes just to see what I liked. Somewhere along the way, Gedit---the program I use more than any---started loading two different icon themes on the open (i.e. Ctrl-O) prompt. I attached an image of it in this post. 

The right pane loads the correct icon theme. The left pane (which doesn't square with the left pane on Nautilus, if I remember how it worked on 12.10 correctly) is using High Contrast (I think). The issue here is minor, but I'm hoping I can get some help on how to correct it. Thanks for any and all help.

---

### Post by Dennis N on 2015-06-20
Both are the result of the icon search specifications. Essentially, the icon needed (purpose and and size) is not in the current theme, so the parent theme is used.

Quote from Gnome "Icon Theme Specification":

>  The lookup is done first in the current theme, and then recursively in each of the current theme's parents, and finally in the default theme called "hicolor" (implementations may add more default themes before "hicolor", but "hicolor" must be last). As soon as there is an icon of any size that matches in a theme, the search is stopped. Even if there may be an icon with a size closer to the correct one in an inherited theme, we don't want to use it. Doing so may generate an inconsistant change in an icon when you change icon sizes (e.g. zoom in).

The lookup inside a theme is done in three phases. First all the directories are scanned for an exact match, e.g. one where the allowed size of the icon files match what was looked up. Then all the directories are scanned for any icon that matches the name. If that fails we finally fall back on unthemed icons. If we fail to find any icon at all it is up to the application to pick a good fallback, as the correct choice depends on the context. 


[http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html](http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html) > Icon Lookup

---

