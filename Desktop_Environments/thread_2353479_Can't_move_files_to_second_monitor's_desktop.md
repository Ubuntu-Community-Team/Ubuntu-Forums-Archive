---
title: "Can't move files to second monitor's desktop"
date: 2017-02-22
forum: Desktop Environments
---

### Post by daniel.merino on 2017-02-22
Hi everybody.

I'm using Ubuntu 16.04 LTS with two monitors "Lenovo Group Limited 22''". I'm also using Compiz Settings.

I have a set of files divided in both monitors desktops. After the last update, all the files went put into the left desktop. I can still use the right desktop to place windows and the Unity launcher starts there also, but dropping the files don't work, neither the right-click button to create a new file (only the option "change desktop image" is available in right monitor's desktop). If I change the desktop image, it changes for both monitors.

Another weird thing: when I restart, in the login screen, the monitors seems to be inverted. In the right monitor, the right border connects with the left border of the left monitor. This wasn't happening before.

This is annoying and I can't find anyone with the same issue in these forums. Please, if you need more info about my system, just ask me.

Thanks in advance.
Best regards.

I think that this is the change that has caused this:

```
Start-Date: 2017-02-22  09:01:42
Commandline: aptdaemon role='role-commit-packages' sender=':1.91'
Install: linux-headers-4.4.0-64:amd64 (4.4.0-64.85, automatic), linux-image-4.4.0-64-generic:amd64 (4.4.0-64.85, automatic), linux-image-extra-4.4.0-64-generic:amd64 (4.4.0-64.85, automatic), linux-headers-4.4.0-64-generic:amd64 (4.4.0-64.85, automatic)
Upgrade: linux-headers-generic:amd64 (4.4.0.62.65, 4.4.0.64.68), linux-libc-dev:amd64 (4.4.0-62.83, 4.4.0-64.85), linux-image-generic:amd64 (4.4.0.62.65, 4.4.0.64.68), tcpdump:amd64 (4.7.4-1ubuntu1, 4.9.0-1ubuntu1~ubuntu16.04.1), gstreamer1.0-libav:amd64 (1.8.3-1ubuntu0.1, 1.8.3-1ubuntu0.2), linux-generic:amd64 (4.4.0.62.65, 4.4.0.64.68)
End-Date: 2017-02-22  09:03:20

Start-Date: 2017-02-22  09:09:36
Commandline: aptdaemon role='role-upgrade-system' sender=':1.85'
Upgrade: virtualbox-dkms:amd64 (5.0.24-dfsg-0ubuntu1.16.04.1, 5.0.32-dfsg-0ubuntu1.16.04.2)
End-Date: 2017-02-22  09:12:34
```

---

### Post by daniel.merino on 2017-02-23
I have solved it disabling Nemo. With Nautilus it works fine. So it seems a Nemo bug.

Thanks anyway.

EDIT: I know the exact cause of my issue. It seems that Nemo was updated to latest version and, by default, it has this new setting:

> option to choose on which monitor to show the desktop folder (icons). This can be changed via Dconf Editor (org > nemo > desktop > desktop-layout), and can be set to show desktop icons on primary monitor, on remaining monitors, or on all monitors (default is primary only).

Entering dconf and turning the property to true:true solves the issue.

---

