---
title: "Remove mounted SD card icon from launcher."
date: 2016-10-02
forum: Desktop Environments
---

### Post by cdysthe on 2016-10-02
Hi, 

I have a SD card which is always mounted from fstab on my laptop. There's an icon in the launcher for the mounted SD card. Is itpossible somehow to not have the launcher icon but still have the card mounted just like for the built in disk?   I'm on Unity in Ubuntu 16.04.

---

### Post by CantankRus on 2016-10-02
SD cards don't give you the option to unlock from launcher in right click menu?

---

### Post by sudodus on 2016-10-03
I think it works like this:

- If you mount the SD card to a mountpoint in **/media**, an icon will be displayed

- If you mount the SD card to another mountpoint, for example in **/mnt**, there will be no icon.

---

### Post by cdysthe on 2016-10-03
> **sudodus said:**
> I think it works like this:

- If you mount the SD card to a mountpoint in **/media**, an icon will be displayed

- If you mount the SD card to another mountpoint, for example in **/mnt**, there will be no icon.

And I have mounted it as 'Media". I will try to change that, thanks!

---

