---
title: "dual monitors xorg.conf"
date: 2007-07-07
forum: Desktop Effects &amp; Customization
---

### Post by ray-in-ojai on 2007-07-07
[SIZE="4"]After fooling around I had edited xorg.conf and added a line in the config file. When I reboot its no longer happy. All I have now is a command prompt. 2 questions:  1;  how do I edit xorg.conf so I can remove the line I added, please remember I can no longer get to my desktop, just a command prompt when I reboot. 2; I had made a backup of xorg.conf called xorg.conf_backup how can I rename this file to xorg.conf. again remember I have to do this from the command prompt I can no longer get to the desktop.
Thanks,
Ray
[/SIZE]

---

### Post by hyperair on 2007-07-07
```

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

```

---

