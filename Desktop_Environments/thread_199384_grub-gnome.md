---
title: "grub-gnome"
date: 2006-06-18
forum: Desktop Environments
---

### Post by yamca on 2006-06-18
Hi everyone;
I made a stupid thing and resize my linux partition from winxp using partition magic. Then i lost grub. Then reinstalled it. I did not format any partitions.
When i boot ubuntu i saw that i lost my icons and wallpaper. Eveything turned back to default gnome. I did not format home partition but i cant find my files.

---

### Post by sopo_dan on 2006-06-18
looks like your /home partition isn't mounted
if you say that you tinkered with partitions, you should check /etc/fstab to see if the references there are still correct and update them if necessary

---

