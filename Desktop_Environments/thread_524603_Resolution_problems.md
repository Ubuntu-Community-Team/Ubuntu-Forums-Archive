---
title: "Resolution problems"
date: 2007-08-13
forum: Desktop Environments
---

### Post by Tomkin on 2007-08-13
I don't know if this belongs here, but here goes:

I have a 15.4" widescreen monitor, whose default resolution is 1280 x 768, I believe. I am currently using Kubuntu Feisty Fawn, and when I went to change the resolution from 1024*768 (which it was set at), I found that it would not allow me to go any higher. When I switch to a lower, widescreen resolution, I end up with a bunch of black space on the edges.

Being the very new user that I am, I'm kinda stumped about this, but I'm sure this problem has happened before. If anyone could tell me how to change the resolution back up to 1280*768, I'd be very grateful. Thanks!

 - Tomkin

---

### Post by be4truth on 2007-08-13
open a terminal and type

```
sudo dpkg-reconfigure xserver-xorg
```

Let the wizard help you. If you don't know go with the default answer. At one time is suggest the monitor resolutions. Go to the one you want and mark it by pressing the space bar. Then continue. After you finish your old configuration file will be saved as a backup. Important.
Then reboot your machine and try to set the screen resolution by going into SYSTEM/PREFERENCES/SCREEN RESOLUTION

---

