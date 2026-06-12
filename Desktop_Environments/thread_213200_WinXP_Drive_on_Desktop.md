---
title: "WinXP Drive on Desktop"
date: 2006-07-11
forum: Desktop Environments
---

### Post by scottieblues on 2006-07-11
When I setup my XP Disk to auto mount on boot up, it placed an icon on the desktop as well as under my "places" menu.

How can I get rid of the one on the desktop?

Thanks.

---

### Post by aysiu on 2006-07-11
Alt-F2 ```
gconf-editor
``` Apps > Nautilus > Desktop > Volumes Visible

---

### Post by scottieblues on 2006-07-11
> **aysiu said:**
> Alt-F2 ```
gconf-editor
``` Apps > Nautilus > Desktop > Volumes Visible

Thank you very much.

This forum and this community rocks.

---

### Post by Akula on 2006-07-11
I noted same thing. I edited /etc/fstab so that I did put # in front of lines about my Windows partitions to make sure that nothing 'bad' happens to them.

Don't know if it was a good idea, but it seems to work. =)

---

### Post by Scythe!? on 2006-07-28
I havent touched any settings or anything and mine mounts automatically with desktop shortcut & everything :?:

---

