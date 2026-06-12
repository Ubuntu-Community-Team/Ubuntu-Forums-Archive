---
title: "VNC Server error"
date: 2006-02-06
forum: Desktop Environments
---

### Post by GSMD on 2006-02-06
Hello.
I've configured VNC Server the same way I did under SlackWare, there it worked just fine. But not under Ubuntu 5.10. I get
```
more /var/log/Xorg.0.log |grep vnc
(II) LoadModule: "vnc"
(WW) Warning, couldn't open module vnc
(II) UnloadModule: "vnc"
(EE) Failed to load module "vnc" (module does not exist, 0)
```
And a client can't connect. Has anyone faced and solved such a problem before?
Thank you.

---

### Post by gordyt on 2006-02-06
GSMD I'm running VNC on my AMD64 system.  It was already installed.  I just had to go to System / Preferences / Remote Desktop and enable the sharing options.

--gordon

---

### Post by GSMD on 2006-02-06
Thank you.
It worked out. :)

---

