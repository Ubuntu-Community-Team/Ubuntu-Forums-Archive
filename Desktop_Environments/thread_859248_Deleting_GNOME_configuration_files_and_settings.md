---
title: "Deleting GNOME configuration files and settings"
date: 2008-07-14
forum: Desktop Environments
---

### Post by POW R TOC H on 2008-07-14
I currently have Kubuntu, but I will switch to ubuntu (I'm simply going to install ubuntu-desktop). I did this once, but had problems.
My hard drive has 3 partitions, 20Gb for root, 1Gb for swap, and 160 for /home. When I change distros, I only format the root partition, and I leave /home untouched. This is a salvation most of the time, as this saves even my browser history :)
But, back when I had ubuntu, I messed something up, and GNOME is broken. Now, whenever I install it, it uses old configurations and settings, that are still in my /home directory.
Can you please tell me what dirs contain GNOME configuration files (I have deleted two, but there are some left I can't find) so I can delete them, and get a clean installation of GNOME?
Thank you...

---

### Post by sayakb on 2008-07-14
Removing the contents of ~/.gnome, ~/.gnome2, ~/.nautilus, ~/.gconf should remove most of the settings

---

### Post by VMC on 2008-07-14
> **POW R TOC H said:**
> 
Can you please tell me what dirs contain GNOME configuration files (I have deleted two, but there are some left I can't find) so I can delete them, and get a clean installation of GNOME?
Thank you...

What two did you delete? Have you looked at your ~/home/.gnome2 & .gconf directories? Maybe you could backup and delete them for starters.

---

### Post by POW R TOC H on 2008-07-14
I just deleted .gnome and .gnome2 
Now I have deleted .gconf and .nautilus too
I don't need backup, because I want a clean new gnome :)
Thank you everyone

---

