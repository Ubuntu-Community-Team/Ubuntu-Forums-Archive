---
title: "Flash Drives mount as Read Only"
date: 2013-05-17
forum: Desktop Environments
---

### Post by mrtomcef on 2013-05-17
Let me start off by letting you know that earlier this week I upgraded to Xubuntu 13.04 from Xubuntu 12.10 (both 32bit). 

I have a Patriot flash drive that automatically mounts to /media/tom/patriot Whenever I copy files to the flash drive though the GUI I get an error saying that the destination is read only. 

The interesting part about this problem is that I am still able to copy files to the flash drive using the cp command.

---

### Post by dentaku65 on 2013-05-17
Try to check if you have access enabled for external storage under:
> Setting Manager -> Users and Groups -> <your_username> -> Advanced Settings -> Access external storage devices automatically
and maybe even
> Setting Manager -> Users and Groups -> <your_username> -> Advanced Settings -> Mount user-space filesistem (FUSE)

---

### Post by mrtomcef on 2013-05-20
Thanks for the reply. I double checked those setting and I was able to copy files to the flash drive without any problems.

---

