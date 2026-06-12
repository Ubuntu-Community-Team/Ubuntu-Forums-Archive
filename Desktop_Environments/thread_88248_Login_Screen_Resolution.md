---
title: "Login Screen Resolution"
date: 2005-11-09
forum: Desktop Environments
---

### Post by blouie on 2005-11-09
How do I change the resolution of the login screen?
My system defaults to 1280x1024, and the monitor performance is not consistant at this resolution - some times I get funny mess of screen artifacts; I want to set it at 1024x768.
I changed it inside of gnome, and it is fine, but the login screen remains at 1280x1024.

---

### Post by Remmelas on 2005-11-09
open /etc/X11/xorg.conf in your favorite editor using sudo
```
sudo nano -w /etc/X11/xorg.conf
``` for example if you like using a console editor.
find the area that looks something like this
```
SubSection "Display"
                Depth           24
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection

```
and remove any modes that you don't want to have used.  X will use the first one listed, so if you want 1024x768, use a Modes line like this
```
Modes "1024x768" "800x600" "640x480"
```

---

