---
title: "Can't change text entry since upgrade to Vivid"
date: 2015-05-11
forum: Desktop Environments
---

### Post by nasevz2 on 2015-05-11
Since upgrade to Vivid, I can only use English text entry. I can change text entry indicator using mouse (shortcut is not working), but even if another entry is displayed, English remains active. 
I don't know if it is related, but theme is not consistent in all programs. Firefox, LibreOffice, Skype ... are using icons from another theme and I can’t change it either.
I suspect that the cause of the problem is unity-settings-daemon which creates bug report upon system start up. Tried to reinstall it, but that didn't solve the problem.

---

### Post by dino99 on 2015-05-11
please post the output of > cat /etc/apt/sources.list

---

### Post by fawn93 on 2015-05-11
i'm also experiencing the problem you mentioned. i think this problem is occurred in the laptop. i'm using Hangul. Other programs like Firefox, Libreoffice, there is no problem in transforming Hangul/English text entry
But in Nautilus, text entry is displayed when i change the file name. i think this problem is related with HUD. Whereas HUD is using the shortcut-Left Alt,
the key for changing Hangul/English is using the Right Alt. 
I also don't know how to change the preferences related with HUD

---

### Post by nasevz2 on 2015-05-11
cat /etc/apt/sources.list

```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) vivid-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-backports universe main multiverse restricted
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) utopic-proposed universe main multiverse restricted #Not for humans during development stage of release utopic
deb [http://archive.canonical.com/](http://archive.canonical.com/) vivid partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) vivid partner
deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra
deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) vivid main
# deb-src [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) vivid main
```

---

