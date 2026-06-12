---
title: "Desktop Icons vanished afte last update. 22.04 LTS"
date: 2023-04-10
forum: Desktop Environments
---

### Post by johntelek on 2023-04-10
My destop icons dissapeard after my last update yesterday. Everything is still in my desktop folder
but not appearing on the desktop as shown.

Any ideas anyone ?

JT

---

### Post by chris0nlinux on 2023-04-12
Well, this has to be a problem with the Desktop Icons NG(DING) extension for GNOME. You can try reinstalling it from [https://extensions.gnome.org/](https://extensions.gnome.org/) or try running the command ```
gnome-extensions reset ding@rastersoft.com
```. Let me know if this helps.

P.S.: You should be careful when sharing your desktop as you leaked your location and IP address.

---

### Post by johntelek on 2023-04-19
> **chris0nlinux said:**
> Well, this has to be a problem with the Desktop Icons NG(DING) extension for GNOME. You can try reinstalling it from [https://extensions.gnome.org/](https://extensions.gnome.org/) or try running the command ```
gnome-extensions reset ding@rastersoft.com
```. Let me know if this helps.

P.S.: You should be careful when sharing your desktop as you leaked your location and IP address.

SOLVED SOLVED SOLVED  ;););)

Found this in a Kubuntu forum and it worked. I had to reinstall plasma because when I uninstalled debian qt5 to replace it
with one from the qt installer, it also removed a heap of other stuff and broke things like the file manager with filelight running instead.
[INDENT] Replacing libqt5quick5-gles with libqt5quick5 solved my problem
 [/INDENT] so make a: sudo apt install libqt5quick5 it worked for me on debian

Cheers,
    John.

---

