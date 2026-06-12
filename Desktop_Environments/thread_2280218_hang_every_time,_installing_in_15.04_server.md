---
title: "hang every time, installing in 15.04 server"
date: 2015-05-28
forum: Desktop Environments
---

### Post by bernard13 on 2015-05-28
I get to this point where it is building the settings, and after finding the _*initrd *_image, it goes away forever... days I've waited even (over a weekend)!
removed, reinstall, and same error at same point.
newly installed 15.04 server in a VM (hyperV) so I wanted to add the KDE desktop.  Getting nowhere.
Any ideas?

Update: same issue on Unity or XDE (ubuntu-desktop, xubunu-desktop).
the GRUB script that seems to be hanging is **/etc/grub.d/10-linux** , *at line 323*, the last reported **gettext_printf** "*Found initrd image:*" sent to **>&2**
This is the area it stops performing, and am not sure how to debug further where it is failing.  it does not apparently perform the step echoing the submenu, just below the "found initrd image".

---

