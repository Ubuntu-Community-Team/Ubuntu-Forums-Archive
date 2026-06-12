---
title: "nvidia dual head issue"
date: 2008-05-04
forum: Desktop Environments
---

### Post by italys on 2008-05-04
I finally got both monitors to work in ubuntu, however it is not displaying it the way I wish. I don't want the entire screen to be centered across both displays. Instead, I want an empty display on my right display and the left display will be my desktop. I had it set up before, but I installed some X stuff recently and it stopped functioning. I have twinview disabled.

---

### Post by warp99 on 2008-05-05
> **italys said:**
> I finally got both monitors to work in ubuntu, however it is not displaying it the way I wish. I don't want the entire screen to be centered across both displays. Instead, I want an empty display on my right display and the left display will be my desktop. I had it set up before, but I installed some X stuff recently and it stopped functioning. I have twinview disabled.
You can run 'sudo nvidia-settings' to reset this, then use the 'Save to X Configuration' dialog. If you don't have nvidia-settings installed enable the universe repository then:
```
sudo apt-get install nvidia-settings
```
and remember to backup you /etc/X11/xorg.conf file before you try this at home, mio amico capisci?

---

