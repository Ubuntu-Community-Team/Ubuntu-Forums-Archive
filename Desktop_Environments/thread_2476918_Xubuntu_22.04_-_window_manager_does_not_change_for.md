---
title: "Xubuntu 22.04 - window manager does not change for all apps"
date: 2022-07-11
forum: Desktop Environments
---

### Post by przemnet on 2022-07-11
Hi,

I've noticed that when I change Window Manager to Numix in Xubuntu 22.04, this change does not apply for all apps.

As you can see on attached picture, windows on the left (file explorer, terminal) are using Numix Windows Manager and apps on the right are using default Window Manager. In 20.04 it was not an issue - after the change, Numix was used by all apps.

Does anyone know how to fix it in 22.04?


Thanks,
Przemek

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290713&stc=1[/IMG]

---

### Post by przemnet on 2022-07-12
Hi,

I received help on XFCE forum [https://forum.xfce.org/viewtopic.php?pid=68012](https://forum.xfce.org/viewtopic.php?pid=68012) and the solution was to install gtk3-nocsd package:
```
sudo apt update && sudo apt install gtk3-nocsd
```

Cheers,
Przemek

---

