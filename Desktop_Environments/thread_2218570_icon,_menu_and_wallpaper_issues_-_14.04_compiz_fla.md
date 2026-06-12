---
title: "icon, menu and wallpaper issues - 14.04 compiz flashback"
date: 2014-04-21
forum: Desktop Environments
---

### Post by odhoenator on 2014-04-21
Hi, I'm using 14.04 64-bit, and have a few general desktop environment-type quirks in flashback-compiz that I'd like to sort out if I can. Red numbers in the picture relate to the issues below.

[IMG]http://i.imgur.com/XcjE3GC.jpg?1[/IMG]

1. Gaps between shortcut icons. In 12.04 these all sat right up against eah other - how do I get these to sit closer together?

[s]2. Icons aren't showing properly in the menus - you will see from the image that many icons, particularly in the Applications drop-down are just grey rectangles. How do I get these to display properly?[/s] - solved by installing a new icon set.

3. The menu has a ton of links that I don't need, and is missing some that I do (Wine, in particular). I've tried editing this using the Main Menu tool in System Tools -> Preferences, and while my changes seem to get saved, it doesn't change anything in the menu I see.

4. Not strictly a glitch, but I'm using Wally as a wallpaper changer. Each time the background changes, it briefly shows one of the default Ubuntu backgrounds. How can I stop this? When I go to System Tools -> Preferences -> Appearance, it only shows whichever wallpaper Wally has selected.

---

### Post by cmcanulty on 2014-04-21
The grey icons show up when an item was installed previously but is now not installed. Perhaps you upgraded and they are old versions. Try writing down the grey ones and installing those apps from synaptic.

---

### Post by odhoenator on 2014-04-21
> **cmcanulty said:**
> The grey icons show up when an item was installed previously but is now not installed. Perhaps you upgraded and they are old versions. Try writing down the grey ones and installing those apps from synaptic.

Heya, I tried changing icon sets, and that seems to have worked - looks like certain icon sets are just borked for me. I've installed one that I like and it's working. Thanks!

---

### Post by kansasnoob on 2014-05-06
Regarding number 3 I encountered a similar problem using flashback w/metacity during Trusty dev:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1267787](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1267787)

After that was fixed (somewhat fixed) a new bug cropped up:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1305348](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1305348)

But that should be fixed if you have the current versions of these packages:

```
lance@lance-desktop:~$ apt-cache policy **gnome-panel**
gnome-panel:
  Installed: 1:3.8.0-1ubuntu11
  Candidate: 1:3.8.0-1ubuntu11
  Version table:
 *** 1:3.8.0-1ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
        100 /var/lib/dpkg/status
lance@lance-desktop:~$ apt-cache policy **alacarte**
alacarte:
  Installed: 3.10.0-1ubuntu2
  Candidate: 3.10.0-1ubuntu2
  Version table:
 *** 3.10.0-1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
        100 /var/lib/dpkg/status
lance@lance-desktop:~$ apt-cache policy **gnome-menus**
gnome-menus:
  Installed: 3.10.1-0ubuntu2
  Candidate: 3.10.1-0ubuntu2
  Version table:
 *** 3.10.1-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by odhoenator on 2014-05-07
> **kansasnoob said:**
> Regarding number 3 I encountered a similar problem using flashback w/metacity during Trusty dev:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1267787](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1267787)

After that was fixed (somewhat fixed) a new bug cropped up:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1305348](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1305348)

But that should be fixed if you have the current versions of these packages:

```
lance@lance-desktop:~$ apt-cache policy **gnome-panel**
gnome-panel:
  Installed: 1:3.8.0-1ubuntu11
  Candidate: 1:3.8.0-1ubuntu11
  Version table:
 *** 1:3.8.0-1ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
        100 /var/lib/dpkg/status
lance@lance-desktop:~$ apt-cache policy **alacarte**
alacarte:
  Installed: 3.10.0-1ubuntu2
  Candidate: 3.10.0-1ubuntu2
  Version table:
 *** 3.10.0-1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
        100 /var/lib/dpkg/status
lance@lance-desktop:~$ apt-cache policy **gnome-menus**
gnome-menus:
  Installed: 3.10.1-0ubuntu2
  Candidate: 3.10.1-0ubuntu2
  Version table:
 *** 3.10.1-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status

```

Thanks for replying kansasnoob. I had a look through your first link, but the only fix I could see mentioned was to use alacarte. I've used that (after updating/reinstalling gnome-menus, gnome-panel and alacarte), but that doesn't have any effect. Alacarte has saved my menu configuration, as all the right things are already checked and unchecked when I run it - it just doesn't look anything like the menu I actually have.

---

### Post by kansasnoob on 2014-05-08
Sorry I wasn't very clear in my first post :(

Please post the output of the following commands:

```
apt-cache policy gnome-panel
```

```
apt-cache policy alacarte
```

```
apt-cache policy gnome-menus
```

---

### Post by odhoenator on 2014-05-10
Thank you kansas!

apt-cache policy gnome-panel:

```
gnome-panel:
  Installed: 1:3.8.0-1ubuntu12
  Candidate: 1:3.8.0-1ubuntu12
  Version table:
 *** 1:3.8.0-1ubuntu12 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     1:3.8.0-1ubuntu11 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
```

apt-cache policy alacarte:

```
alacarte:
  Installed: 3.10.0-1ubuntu2
  Candidate: 3.10.0-1ubuntu2
  Version table:
 *** 3.10.0-1ubuntu2 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
```

apt-cache policy gnome-menus:

```
gnome-menus:
  Installed: 3.10.1-0ubuntu2
  Candidate: 3.10.1-0ubuntu2
  Version table:
 *** 3.10.1-0ubuntu2 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

