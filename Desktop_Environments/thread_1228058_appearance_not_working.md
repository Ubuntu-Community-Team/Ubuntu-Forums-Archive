---
title: "appearance not working"
date: 2009-07-31
forum: Desktop Environments
---

### Post by DrClaw27 on 2009-07-31
I have been 9.04 in vmware for a while now and connect to it with nxlinux from work. It was working fine until I ran some of the latest patches and now the window decoration don't seem to be working. I can make changes under system-preferences-appearance and it changes the the current window but not the taskbar or any other programs. Anyone have an ideas?

---

### Post by gettinoriginal on 2009-07-31
Which window decorator are you using, ie GTK, emerald, etc.  Which ever you are using:
```
emerald --replace
gtk-window-decorator --replace
```

---

