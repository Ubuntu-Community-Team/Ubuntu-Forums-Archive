---
title: "Ubuntu 12.04 Gnome Shell Panels do not show up in workspaces 2, 3 or 4"
date: 2012-06-25
forum: Desktop Environments
---

### Post by pabloikba on 2012-06-25
New install of Ubuntu 12.04 with gnome shell. Getting used to it but in Workspaces 2, 3 & 4 - there is no top nor bottom panel like I have in Workspace 1. It is just a big old screen with a background like in Workspace 1. No way to get back to Workspace 1 other than CTRL-ALT-DEL....

Any ideas?

Thanks

Pablo

---

### Post by markbl on 2012-06-25
How many screens do you have attached? Does ctrl+alt+up/down work, and from any workspace, including workspace 1? In workspace 1, do you see workspace 2 in activities overview? Are you using any related ppas, e.g. gnome3 team and/or ricotz ppa?

---

### Post by pabloikba on 2012-06-25
Thanks for your reply. I appreciate it.

I have only one screen attached. Ctrl-Alt-Up/Down or Left/Right does not work. I used to use that on 10.10.
I'm using Gnome Shell so I am not sure what Activities View is...but, on the bottom panel at the far right I see the little boxes for 4 workspaces. I tried to set them to 4x1 but they still come up as 4 little boxes - 2 on top of 2.

When I go to another workspace, the only way I've found of getting back to workspace 1 is to Ctrl-Alt-Del....it switches me right back. I would love to have the top and bottom panels replicated on all workspaces.

Pablo

---

### Post by markbl on 2012-06-26
I don't think you are using gnome shell? The activities overview is fundamental to gnome shell. That is the scale view of windows you see when you press the super key, or use the top left mouse hotspot. It is how you change between tasks/windows in gnome shell and how you see the scaled other workspaces. Also, gnome shell only uses vertical "dynamic" workspaces, so only ctrl+alt+up/down, NOT left/right. If you are seeing a tiny scale view of a 2 by 2 workspaces then that sounds like another traditional desktop environment, not gnome shell. Gnome shell looks like [this](https://live.gnome.org/GnomeShell/Screenshots), although the default ambiance theme on ubuntu gnome shell looks better than that which is the default gnome theme.

---

### Post by kansasnoob on 2012-06-26
> **pabloikba said:**
> Thanks for your reply. I appreciate it.

I have only one screen attached. Ctrl-Alt-Up/Down or Left/Right does not work. I used to use that on 10.10.
I'm using Gnome Shell so I am not sure what Activities View is...but, on the bottom panel at the far right I see the little boxes for 4 workspaces. I tried to set them to 4x1 but they still come up as 4 little boxes - 2 on top of 2.

When I go to another workspace, the only way I've found of getting back to workspace 1 is to Ctrl-Alt-Del....it switches me right back. I would love to have the top and bottom panels replicated on all workspaces.

Pablo

I agree with *markbl*'s last comment, this sounds more like Gnome classic than gnome-shell.

There are two classic sessions, Gnome classic which uses Compiz and Gnome classic (no effects) which uses Metacity.

I've found that the standard classic session is a mess, but the classic (no effects) session works quite well. I've been making some notes about the latter here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

### Post by pabloikba on 2012-06-26
Kansasnoob - you're right....I am using gnome-classic w/compiz.

I am going to follow your posting and report back - thanks for responding to my query.

Pablo

---

### Post by pabloikba on 2012-06-26
Kansasnoob,

I have followed your posting about gnome-classic and now 12.04 is "like it should be". Many thanks for taking the time to respond to me.

Pablo

---

### Post by pabloikba on 2012-06-26
I have a question about the gnome-class no-effects....

When I start a program like T-bird or Firefox or Libre office, etc, I am used to seeing it in the lower panel in a notification area. They do not show up. If I minimize them they disappear. 

Am I missing something?

Pablo

---

### Post by pabloikba on 2012-06-27
Kansasnoob,

Can't figure out how to get bottom (or top panel to show current open applicatons. I can open Tbird, Firefox, etc., and if I minimize them I can't get them back....screenshot attached.

Suggestions, please?

Thanks,

Pablo

---

### Post by markbl on 2012-06-27
Pabloikba, please change the title of this thread from Gnome Shell to Gnome Classic otherwise it will confuse the hell out of other people.

---

### Post by pabloikba on 2012-06-28
Thanks everyone. 
I've solved my problem by switching to Cinnamon.

Pablo

---

