---
title: "xmonad is stretched over two screens"
date: 2011-11-23
forum: Desktop Environments
---

### Post by datr on 2011-11-23
I installed xmonad as described here:
[http://markhansen.co.nz/xmonad-ubuntu-oneiric/](http://markhansen.co.nz/xmonad-ubuntu-oneiric/)

But found that xmonad was only using one of my two screens so I edited xorg.conf to set:
    Option         "Xinerama" "true"
in the ServerLayout section.

Now xmonad uses both screens but rather than a separate workspace on each I get one stretched over the two of them. This doesn't seem to be the expected functionality from what I can gather from the xmonad site. Does anyone have any idea what might be causing this?

-d

---

