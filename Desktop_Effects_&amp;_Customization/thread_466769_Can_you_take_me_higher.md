---
title: "Can you take me higher?"
date: 2007-06-07
forum: Desktop Effects &amp; Customization
---

### Post by honeysmooth on 2007-06-07
Just installed Ubuntu 7.04 and I love it. The only problem is I cannot take my resolution higher than 1024x768. I have enabled the ATI restricted drivers and I just don't know what else I can do. Thanks in advance for any help!

---

### Post by renzokuken on 2007-06-07
from the terminal run

```
sudo cp /etcX11/xorg.conf /etc/X11/xorg.cong_backup
``` to backup your current xorg.conf

then

```
sudo dpkg-reconfigure xserver-xorg
```

leave everything as it is till you get to the "resolutions" screen. select the resolutions you want, then carry on leaving things as default.

restart X (Ctrl+Alt+Backspace) or reboot and see if your new resolutions are available

---

