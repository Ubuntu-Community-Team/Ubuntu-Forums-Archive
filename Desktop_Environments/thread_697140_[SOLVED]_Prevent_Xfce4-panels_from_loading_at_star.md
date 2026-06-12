---
title: "[SOLVED] Prevent Xfce4-panels from loading at startup"
date: 2008-02-14
forum: Desktop Environments
---

### Post by chochem on 2008-02-14
To exploit a [GNOME specific panel hack]("http://ubuntuforums.org/showthread.php?t=404885") I installed the GNOME panel (uhm manager? controller? thingy?) alongside Xubuntu's xfce4-panel... thingy. 

However after having rearranged the desktop a bit, I find I no longer need xfce4-panel, relying instead on a single GNOME-panel. So I was wondering where the settings that loaded thingies like xfce4-panel were located so I could disable it (so I don't have to kill it every time I boot up).

Thanks in advance.

EDIT:
Answer: Depend on xfce4 session manager to save the new setup when you quit or manually edit xinitrc (type 'man startxfce4' in terminal for more info)

---

