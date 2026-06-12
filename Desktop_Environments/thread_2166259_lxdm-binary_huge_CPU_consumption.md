---
title: "lxdm-binary huge CPU consumption"
date: 2013-08-08
forum: Desktop Environments
---

### Post by asc3 on 2013-08-08
I got an issue similar to described here:
[http://ubuntuforums.org/showthread.php?t=1892232](http://ubuntuforums.org/showthread.php?t=1892232)
[https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/901407](https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/901407)

In a short: lxdm-binary on Ubuntu 12.04.2 LTS, 8 Aug. 2013, on GMA500 Poulsbo platform may have 50%-100% infinite CPU consumption.

Workaround:

Logout/close any graphical interface/desktop session. Press Ctrl+Alt+F1, enter user name and password. Then remove LXDM, install GDM (or another GUI session login tool):
```

sudo -i
apt-get remove lxdm
apt-get install gdm
service gdm restart

```

You may want to press Ctrl+Alt+F1 again end enter command *exit* twice. In order to leave "root" environment and close TUI session, where sudo credentials are stored for some minutes. You may reboot instead.

Key-words/tags: LXDE, lxde-binary, huge, CPU consumption.

---

