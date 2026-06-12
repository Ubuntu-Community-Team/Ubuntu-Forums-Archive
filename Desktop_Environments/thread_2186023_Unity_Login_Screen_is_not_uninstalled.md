---
title: "Unity Login Screen is not uninstalled"
date: 2013-11-05
forum: Desktop Environments
---

### Post by limestorm on 2013-11-05
I uninstalled Unity completely and installed Cinnamon in its place, but the login screen still shows the Unity theme.How do I get rid of this and replace it with a different login screen?

---

### Post by grahammechanical on 2013-11-05
What you are seeing is not the Unity login screen but the Light Display Manager (lightdm) login screen. Lightdm shows either the background wallpaper that we choose or the default Ubuntu background wallpaper if we select to have a rotating background image. The default Ubuntu background image is called warty-final-ubuntu.png and you can find it at /usr/share/backgrounds along with all the other background images.

---

### Post by limestorm on 2013-11-05
Thank you!

---

