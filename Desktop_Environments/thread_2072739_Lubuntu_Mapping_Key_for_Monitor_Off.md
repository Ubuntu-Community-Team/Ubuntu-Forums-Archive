---
title: "Lubuntu Mapping Key for Monitor Off"
date: 2012-10-18
forum: Desktop Environments
---

### Post by mikeym on 2012-10-18
Hi,

I'm trying to set up the *Fn* Keys for my Eeepc to Work in *lubuntu*. I've got them working where the key already has a key symbol matched to it, by setting the key symbol to a shortcut in my *~/.config/openbox/lubuntu-rc.xml*. So for example my task manager key (Fn+F9) is automatically mapped to *XF86Launch1* so I added:

```

    <!-- Fn+F9 -->
    <keybind key="XF86Launch1">
      <action name="Execute">
        <command>lxtask</command>
      </action>
    </keybind>

```

But I can't seem to get this to work for Monitor Off (Fn+F7) which is unbound on my keyboard (keycode 252). I've tried binding it in *~/.Xmodmap* to *XF86Launch7*:

```

! ~/.Xmodmap
! !
! keycode xxx = XF86ZoomIn
! keycode xxx = XF86ZoomOut
! keycode xxx = XF86Back
! keycode xxx = XF86Forward
keycode 252 = XF86Launch7

```

This appears to work according to *xev* but it wont work in openbox (LXDE) with the following:

```

    <!-- Fn+F7 bound in ~/.Xmodmap from keycode 252 to XF86Launch7 -->
    <keybind key="XF86Launch7">
      <action name="Execute">
        <command>/home/XXXXXXXX/bin/monitor-off.sh</command>
      </action>
    </keybind>

```

Where */home/XXXXXXXX/bin/monitor-off.sh* is:

```

#!/bin/bash
sleep 2; xset dpms force off

```

I've even tried changing the keybind key in my rc.xml above to be a sequence "C-A-S" and that works, so the problem doesn't appear to be the script.

Does anyone have any ideas how to make this key work?

---

