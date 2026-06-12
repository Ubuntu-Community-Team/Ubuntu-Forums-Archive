---
title: "UbuntuGnome 14.04 Gnome-Classic doesn't work"
date: 2014-05-21
forum: Desktop Environments
---

### Post by turkel.christopher on 2014-05-21
I am using UbuntuGnome 14.04 and when I try to log into Gnome Classic I just get a black screen, no panels or windows, nothing. Clicking doesn't do anything.

---

### Post by kansasnoob on 2014-05-22
Please post the output of this command:

```
apt-cache policy gnome-shell-extensions
```

---

### Post by turkel.christopher on 2014-05-22
```
apt-cache policy gnome-shell-extensions
gnome-shell-extensions:
  Installed: 3.10.1-0ubuntu2
  Candidate: 3.10.1-0ubuntu2
  Version table:
 *** 3.10.1-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status



```

---

### Post by kansasnoob on 2014-05-22
Hmmm, I thought maybe you had added a later version via PPA but I see that's not the case.

Does the standard GNOME session run OK?

I'd only had trouble with the new "classic" session when I mucked about with gnome 3.12.

---

### Post by turkel.christopher on 2014-05-23
It was weirder than that. During an install of Wine from the ppa something changed. I spent a couple of hours on IRC figuring this out. Purged wine, reinstalled, gnome classic works fine.

---

