---
title: "UniChrome integrated video"
date: 2005-07-03
forum: Desktop Environments
---

### Post by dc2447 on 2005-07-03
I recently built a new system which has a via chipset and onboard video with S3 UniChrome integrated video - I stuck FC4 non there (it's my distro of choice) but the video will only go to 800 * 600 - further reading made me think that I had to start compiling kernel modules to get proper support.

But, I stuck Kubunu on there and 30 minutes later I'm up and running with 1280 *1024 out of the box.

How can this be? Both are running similar kernels and pretty much the same version of xorg.

---

### Post by Tomy on 2005-07-03
You are probably running the vesa driver not the via driver on Ubuntu hoary. S3 Unichrome drivers are not yet fully supported. DRI (direct rendering infastructure) does not work yet, the ubuntu via driver is quite flakey. DRM (direct rendering module) for via is not in the linux 2.6.10 kernel that ships with hoary.

Hopefully the next Ubuntu release, breezy badger, will fully support S3 Unichrome.

---

### Post by dc2447 on 2005-07-03
[QUOTE=Tomy]You are probably running the vesa driver not the via driver on Ubuntu hoary. S3 Unichrome drivers are not yet fully supported. DRI (direct rendering infastructure) does not work yet, the ubuntu via driver is quite flakey. DRM (direct rendering module) for via is not in the linux 2.6.10 kernel that ships with hoary.

Hopefully the next Ubuntu release, breezy badger, will fully support S3 Unichrome.[/QUOTE]

Intresting.

I must say I was very impressed that it was supported at all.  In fact I am very impressed with Ubuntu's hardware support so far.

---

