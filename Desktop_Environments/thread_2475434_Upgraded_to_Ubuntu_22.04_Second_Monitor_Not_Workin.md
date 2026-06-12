---
title: "Upgraded to Ubuntu 22.04 Second Monitor Not Working"
date: 2022-05-26
forum: Desktop Environments
---

### Post by afmkelvin on 2022-05-26
I upgraded to the new version of Ubuntu 22.04 now my second monitor is not recognized at all. It was recognized in the previoius version. My GPU is an NVidia GeForce GTX 1060. I've been trying everything for hours now to get it to work. I even switch the order in which the monitors are plugged in. And even tried to have the monitor that's not been recognized boot up by itself but it never turned on. Please help.

---

### Post by ActionParsnip on 2022-05-29
Does the system have a make and model?
Did you try uninstalling the Nvidia driver. In my experience the Nvidia driver rarely works after a release change and needs reinstalling.

---

### Post by sudodus on 2022-05-29
Also, please try after switching from Wayland to Xorg. It made my external monitor work in a laptop (with nvidia graphics) with 22.04 LTS.

See [this link](https://askubuntu.com/questions/1406844/ubuntu-22-04-fresh-installation-firefox-will-no-load/1406857#1406857) with instructions to switch to Xorg.

---

