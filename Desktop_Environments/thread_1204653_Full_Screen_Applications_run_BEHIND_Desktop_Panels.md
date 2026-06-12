---
title: "Full Screen Applications run BEHIND Desktop Panels"
date: 2009-07-05
forum: Desktop Environments
---

### Post by Tindytim on 2009-07-05
I have a similar issue as in this thread:
[http://ubuntuforums.org/showthread.php?p=7502481](http://ubuntuforums.org/showthread.php?p=7502481)

However, the legacy fullscreen option doesn't span across multiple monitors like it would normally. I've tried the various hide options, but they are still visible in some form or another. The manual method does well enough, but having to hide and reveal before and after use of certain applications seems rather silly to me.

What other methods are there that I could use? Perhaps a script a could use for my full screen applications?

Any input would be extremely helpful.

---

### Post by Tindytim on 2009-07-05
Well, I solved this one myself.

Rather than attempt to get the application ontop, I simply removed the bars with this script.

```
gconftool-2 --set "/apps/panel/toplevels/top_panel_screen0/unhide_delay" --type integer "100000"
gconftool-2 --set "/apps/panel/toplevels/top_panel_screen0/auto_hide" --type bool "true"
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_screen0/unhide_delay" --type integer "100000"
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_screen0/auto_hide" --type bool "true"
#Your application of choice
blender -W
gconftool-2 --set "/apps/panel/toplevels/top_panel_screen0/unhide_delay" --type integer "0"
gconftool-2 --set "/apps/panel/toplevels/top_panel_screen0/auto_hide" --type bool "false"
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_screen0/unhide_delay" --type integer "0"
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_screen0/auto_hide" --type bool "false"
```

---

