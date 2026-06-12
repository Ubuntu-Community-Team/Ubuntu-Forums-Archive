---
title: "Backup Desktop panels and look"
date: 2008-03-26
forum: Desktop Environments
---

### Post by u-slayer on 2008-03-26
Everytime I reinstall ubuntu I have to spend half an hour fixing the panels and themes to make everything look how I want it too. I found a program called gnome-reset which is supposed to backup all this stuff, but all it does is leave mean with a gzip file and no option to restore, only reset.

Here is what's in the backup file, if anyone knows what to do with these files.

```
ubuntu@ubuntu:/gnome-reset-data$ tree -sh
.
|-- [  15]  domain_list
|-- [  80]  gnome-panel
|   `-- [  80]  %home%
|-- [ 21K]  gnome-panel.entries
`-- [ 528]  ui.entries

```

Is there any other script or program that will automatically backup my Desktop look?:)

---

### Post by Tews on 2008-03-26
Try Quick Start ... It will do exactly what you want it to do .. Read about it here .... [http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

---

