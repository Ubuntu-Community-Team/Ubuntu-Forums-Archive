---
title: "How can I reinstall grub on my /boot partition?"
date: 2009-01-19
forum: General Help
---

### Post by jazzman14 on 2009-01-19
So I've been running solely linux for quite a while now, but had to install windows for a few work and school things. So I installed it on an empty 20GB partition on my single hard disk. So the computer would boot directly into windows without any choice, so I went into gparted (livecd) and changed the boot flags from the windows partition to my /boot partition. This did nothing, it would give me "error loading operating system" so i then went back into gparted and deleted the /boot partition and created a new ext2 partition and flagged it as boot, I then went to the command line and tried to reinstall grub, but when I reload my computer, all that reloads is a grub console. Why is this?

---

### Post by aschwerin.moses on 2009-01-19
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

