---
title: "visual corruption of some qt apps in gnome"
date: 2010-05-20
forum: Desktop Environments
---

### Post by gerryAU on 2010-05-20
G`Day, I`m getting corruption of some kde apps in gnome. While k3b & vlc look fine, others like KRDC & kolourpaint are corrupted. Problem remains if I enable compiz or not.

Ubuntu 10.04 nvidia card . Have two boxes (32 & 64 bit) both with nv cards, and problem happens on both.I have used systemsettings to set AA fonts, but to no avail.

thanks.

[IMG]http://i.imagehost.org/0146/Screenshot-1_6.png[/IMG]

---

### Post by gerryAU on 2010-06-08
Managed to solve it with a tip from this thread.

[http://ubuntuforums.org/showthread.php?t=1318506]("http://ubuntuforums.org/showthread.php?t=1318506")

```

export XLIB_SKIP_ARGB_VISUALS=1 && kolourpaint

```

thanks

---

