---
title: "Xgl and ALT-key"
date: 2006-12-03
forum: Desktop Environments
---

### Post by SirOracle on 2006-12-03
Hi
I have a Dell Latitude D620 with Ubuntu 6.10, and I installed XGL/Compiz following this help:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28Nvidia.29)

All seems to work fine, but every time I press the ALT-key, the active window fly out to the right and put itself on the next workspace. If I for instance try the CTRL+ALT+Right/Left arrow to switch workspace, the active window fly to the right instantly when I touch the ALT-key.

And the workspace switcher seems to only have 1 workspace, and I can't add wokspaces under preferences. But there are 4 workspaces no matter what I set in the workspace switcher preferences.

Has anyone here experienced this? It makes most shortcuts that includes the ALT-key pretty useless, or maybe not useless, but irritating at least ;)

---

### Post by rallymatte on 2006-12-05
Please see
[http://ubuntuforums.org/showthread.php?t=287512&highlight=alt+compiz](http://ubuntuforums.org/showthread.php?t=287512&highlight=alt+compiz)

The solution is to go into gconf-editor and find /apps/compiz/plugins/put/allscreens/options/ and disable put_viewport_right_key and put_viewport_left_key to be disabled.

---

### Post by SirOracle on 2006-12-05
Ahh, works like a charm!! Thank you!

---

