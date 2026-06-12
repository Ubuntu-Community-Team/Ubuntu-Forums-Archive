---
title: "Fonts not displaying in Telegram file download"
date: 2018-11-15
forum: Desktop Environments
---

### Post by Scary Rob on 2018-11-15
Hi guys!

This is a bit of an odd one. I'm running Kubuntu 18.04 and Telegram Desktop version 1.4.3. Today, I went to download a file someone sent me and I got this:

[IMG]https://i.imgur.com/6j0CsG3.png[/IMG]

Fonts are displaying fine on the chat window.

Does anyone have a clue what might be going on here?

---

### Post by Scary Rob on 2018-11-15
Looks like I lost my fight with imgur earlier. Hopefully you can see the image, now.

I didn't have this problem when I downloaded a shared file on 12th November. Here's the apt log for the intervening period:

```
Start-Date: 2018-11-13  06:15:43
Commandline: apt-get dist-upgrade
Requested-By: rob (1000)
Upgrade: nvidia-prime:amd64 (0.8.8.1, 0.8.8.2), ubuntu-drivers-common:amd64 (1:0.5.2.1, 1:0.5.2.2), libglib2.0-bin:amd64 (2.56.2-0ubuntu0.18.04.2, 2.56.3-0ubuntu0.18.04.1), libglib2.0-data:amd64 (2.56.2-0ubuntu0.18.04.2, 2.56.3-0ubuntu0.18.04.1), libglib2.0-0:amd64 (2.56.2-0ubuntu0.18.04.2, 2.56.3-0ubuntu0.18.04.1)
End-Date: 2018-11-13  06:15:50

Start-Date: 2018-11-13  18:00:36
Commandline: apt-get dist-upgrade
Requested-By: rob (1000)
Upgrade: python2.7-minimal:amd64 (2.7.15~rc1-1, 2.7.15~rc1-1ubuntu0.1), libpython2.7:amd64 (2.7.15~rc1-1, 2.7.15~rc1-1ubuntu0.1), python2.7:amd64 (2.7.15~rc1-1, 2.7.15~rc1-1ubuntu0.1), shim-signed:amd64 (1.37~18.04.2+15+1533136590.3beb971-0ubuntu1, 1.37~18.04.3+15+1533136590.3beb971-0ubuntu1), libpython2.7-minimal:amd64 (2.7.15~rc1-1, 2.7.15~rc1-1ubuntu0.1), libpython2.7-stdlib:amd64 (2.7.15~rc1-1, 2.7.15~rc1-1ubuntu0.1)
End-Date: 2018-11-13  18:01:09

Start-Date: 2018-11-14  04:18:01
Commandline: apt-get dist-upgrade
Requested-By: rob (1000)
Install: linux-modules-extra-4.15.0-39-generic:amd64 (4.15.0-39.42, automatic), linux-modules-4.15.0-39-generic:amd64 (4.15.0-39.42, automatic), linux-headers-4.15.0-39-generic:amd64 (4.15.0-39.42, automatic), linux-headers-4.15.0-39:amd64 (4.15.0-39.42, automatic), linux-image-4.15.0-39-generic:amd64 (4.15.0-39.42, automatic)
Upgrade: linux-headers-generic:amd64 (4.15.0.38.40, 4.15.0.39.41), linux-libc-dev:amd64 (4.15.0-38.41, 4.15.0-39.42), linux-image-generic:amd64 (4.15.0.38.40, 4.15.0.39.41), linux-signed-generic:amd64 (4.15.0.38.40, 4.15.0.39.41), linux-generic:amd64 (4.15.0.38.40, 4.15.0.39.41)
End-Date: 2018-11-14  04:19:14

Start-Date: 2018-11-14  15:05:04
Commandline: /usr/bin/unattended-upgrade
Remove: linux-modules-extra-4.15.0-36-generic:amd64 (4.15.0-36.39)
End-Date: 2018-11-14  15:05:37

Start-Date: 2018-11-14  15:05:42
Commandline: /usr/bin/unattended-upgrade
Remove: linux-modules-4.15.0-36-generic:amd64 (4.15.0-36.39), linux-image-4.15.0-36-generic:amd64 (4.15.0-36.39)
End-Date: 2018-11-14  15:06:01

Start-Date: 2018-11-14  15:06:04
Commandline: /usr/bin/unattended-upgrade
Remove: linux-headers-4.15.0-36-generic:amd64 (4.15.0-36.39), linux-headers-4.15.0-36:amd64 (4.15.0-36.39)
End-Date: 2018-11-14  15:06:12

Start-Date: 2018-11-15  02:52:18
Commandline: apt-get dist-upgrade
Requested-By: rob (1000)
Upgrade: libpq5:amd64 (10.5-0ubuntu0.18.04, 10.6-0ubuntu0.18.04.1)
End-Date: 2018-11-15  02:52:20
```

---

### Post by Scary Rob on 2018-11-15
One thing that might be of note - all my other apps are using my dark desktop theme or the specified dark gtk theme on their Save windows. Telegram is the only one generating a save window with a light theme and that icon set.

---

### Post by Scary Rob on 2018-11-27
This has sorted itself out as mysteriously as it started. Marked solved.

---

### Post by Holger_Gehrke on 2018-11-27
Did you perhaps install the snap-version of telegram ? That might explain at least the appearance mismatch; snaps are isolated from the rest of the system (they bring along their own gnome or kde snap because they can't use the one installed in the system) and can't read your theme settings. The self-fixing would then be just an update to the snap(s) which wouldn't get shown in apt logs ...

Holger

---

### Post by Scary Rob on 2018-11-28
Yeah, it is the snap version, and the thought had crossed my mind.

---

