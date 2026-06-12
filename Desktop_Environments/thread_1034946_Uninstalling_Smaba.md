---
title: "Uninstalling Smaba"
date: 2009-01-09
forum: Desktop Environments
---

### Post by raunhar on 2009-01-09
I just installed UBUNTU and installed SAMBA, but was not able to do any sharing . A few days back I had instaled UBUNTU 8.04 on the same machine, but had to format the disk and reinstall a new. That time , Iw as able to connect to my otrher PC's on WIndows XP. But this time I could not do. Do not know why.

I tried to remove SAMBA from APplications-->Add/Remove. It shows SAMBA removed but the folder under /etc still shows. I cannot delete it as it shows no permission to delete.

Pl. suggest

---

### Post by adamlau on 2009-01-09
Remove Samba and its dependencies:

```
sudo apt-get remove samba && sudo apt get autoremove
```

Browse to /etc and remove the samba folder:

```
gksu nautilus
```

Be aware that /etc/samba is created by default on clean installs.

---

