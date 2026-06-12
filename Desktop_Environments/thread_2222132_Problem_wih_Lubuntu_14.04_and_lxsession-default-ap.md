---
title: "Problem wih Lubuntu 14.04 and lxsession-default-apps"
date: 2014-05-05
forum: Desktop Environments
---

### Post by txurrispo on 2014-05-05
Hi to all.

I have one problem, i can´t execute lxsession-default-apps, because said to me "The database is updating, please wait"

If i execute it manually, i get this log:

```
** Message: utils.vala:30: config_path_directory: /home/USER/.config/lxsession-default-apps
** Message: desktop-files-backend.vala:171: test config_path: /home/USER/.config/lxsession-default-apps/settings.conf
** Message: desktop-files-backend.vala:237: Scanning folder: /usr/share/applications
** Message: desktop-files-backend.vala:278: Start scanning


** Message: desktop-files-backend.vala:257: Scanning folder: /usr/share/app-install/desktop
** Message: desktop-files-backend.vala:278: Start scanning


Error: list_files failed: No such file or directory
** Message: desktop-files-backend.vala:333: Finishing scanning


** Message: desktop-files-backend.vala:189: Signal finish scanning with mode: write
** Message: desktop-files-backend.vala:333: Finishing scanning
```

Any help would be appreciated.
Thanks.
Regards.

---

### Post by vasa1 on 2014-05-05
"The database is updating, please wait" seems new to Lubuntu 14.04.

Re. "No such file or directory", do you not have a folder called */usr/share/app-install/desktop*? On my system, that folder has 3085 **.desktop** files!

---

