---
title: "Flickering Screen"
date: 2012-06-03
forum: Desktop Environments
---

### Post by DunnHenry on 2012-06-03
If you are running lubuntu and the screen flickers, you may be able to fix this by running

  sudo dpkg-reconfigure gdm

and switch from lxdm to gdm.

This worked for me. When I use lxdm my screen flickers; when I switch to gdm it stops flickering.

---

