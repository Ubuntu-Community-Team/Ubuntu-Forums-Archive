---
title: "unpredictable behavior for some apps"
date: 2018-08-06
forum: Desktop Environments
---

### Post by escifell on 2018-08-06
Clean install of 18.04.1 onto an XPS13 (9350), previously running 16.04 but upgraded to get better integration with thunderbolt-3 dock. I am running the flashback gnome interface, and home directory is mounted at /local/home as /home is used for my university "home" folder.

Issue - a few of the applications (I have found 2 so far) "Calculator" and "System Monitor" will not run from "Applications" menu (point and click). If I open a terminal "gnome-system-montor" runs OK, but "gnome-calculator" still fails with message:
cannot create user data directory: /local/home/escifell/snap/gnome-calculator/180: Read-only file system

If I look at directory /local/home/escifell/snap/gnome-calculator/180, I have full rwx permissions and can add, edit and delete files.

Advice please.

---

### Post by #&amp;thj^% on 2018-08-06
Default apps are installed in 18.04 through "snap", a new cross-OS package manager. Snap will be much better than APT one day, but right now it's in the beginning stages and experiencing growing pains.

One of these growing pains is that it "themes" each application differently than it has in the past, and some of the new "theming" Also "communitytheme "hasn't had the kinks worked out yet.

Luckily, the workaround is very very easy. Just uninstall with snap and reinstall with APT.

```
sudo snap remove gnome-system-monitor
sudo apt install gnome-system-monitor

```
```
sudo snap remove gnome-calculator
sudo apt install gnome-calculator
```

---

### Post by deadflowr on 2018-08-06
Using home outside /home is a known issue for snaps.
See: [lpbug]1620771[/lpbug]

---

### Post by escifell on 2018-08-15
Thanks installing packages through apt worked.

---

