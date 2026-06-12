---
title: "gnome-panel tries to start"
date: 2011-05-21
forum: Desktop Environments
---

### Post by Jagoly on 2011-05-21
hello. About a week ago I was mucking around trying to get the mint menu working on xubuntu 11.04. I installed alot of dependencies, but in the end could not get it working.

I have now removed everything, including the gnome panel (was a dependency). When added, it was autostarting with xfce. Now, even with it removed, xfce still attempts to autostart it. It's no longer installed, so of course it can't. According to my xfce splashing screen, it's adding about an extra 4 seconds of loading the desktop.

It's not urgent, but four extra seconds of unusable desktop on every boot is a pain.

So basically I'm asking how I would go about stopping it. Thanks.

---

### Post by Toz on 2011-05-22
Have a look at the file ```
~/.cache/sessions/xfce-session-<hostname>\:0
``` where hostname is the hostname of your system. It seems to list all of the applications that start when xfce initializes. I believe you need to edit this file when you are not logged in. Also, make a backup of the file first.

---

