---
title: "X and TWM eog Takes 27 Seconds to Start"
date: 2019-08-27
forum: Desktop Environments
---

### Post by tomdean@speakeasy.org on 2019-08-27
Ubuntu 18.04.3
up-to-date with apt
I have Ubuntu 18.04.3 on /dev/sda.  Newly installed from the DVD.

I do not use the Ubuntu Desktop.
I use X and TWM.  I installed TWM with apt.

At boot time, I select TWM,
  eog /usr/share/icons/hicolor/16x16/apps/evince.png
takes 27 seconds to start.  Top does not show anything taking lots of CPU time.

At boot time, I select Ubuntu,
  eog /usr/share/icons/hicolor/16x16/apps/evince.png
starts immediately.

Is there some tweak I need to do to gnome to fix this?

Tom Dean

---

### Post by cruzer001 on 2019-08-27
You have a xWindow system? I have one too, using spectrwm.

```
systemd-analyze blame
```
Will that give you any clues?

---

### Post by tomdean@speakeasy.org on 2019-08-27
I have another problem.  At boot time, I select TWM, but, get a blank screen.
I use crtl-alt-f3 and login.  I get the expected TWM display with xterms.  Maybe I need to fix that, first?

I do not see any difference between the output of 'systemd-analyze blame' before attempting to start eog, during, or after.
```

p9x79> systemd-analyze blame
          4.365s NetworkManager-wait-online.service
          4.144s plymouth-quit-wait.service
           637ms keyboard-setup.service
           495ms systemd-logind.service
           459ms udisks2.service
           448ms gpu-manager.service
           447ms systemd-journal-flush.service
           415ms systemd-resolved.service
           322ms NetworkManager.service

```

firefox seems to start right away.  Note that gdm3 seems to be running.

This is a new install on a Crucial SSD (really fast).  I did not remove gdm3.

```

p9x79> ps ax | grep -i gdm
 1019     1 Ssl  ?        00:00:00 /usr/sbin/gdm3
 1029  1019 Sl   ?        00:00:00 gdm-session-worker [pam/gdm-launch-environment]
 1050  1029 Ssl+ tty1     00:00:00 /usr/lib/gdm3/gdm-x-session gnome-session --autostart /usr/share/gdm/greeter/autostart
 1052  1050 Sl+  tty1     00:00:00 /usr/lib/xorg/Xorg vt1 -displayfd 3 -auth /run/user/121/gdm/Xauthority -background none -noreset -keeptty -verbose 3
 1062  1050 Sl+  tty1     00:00:00 /usr/lib/gnome-session/gnome-session-binary --autostart /usr/share/gdm/greeter/autostart
 1399  1019 Sl   ?        00:00:00 gdm-session-worker [pam/gdm-password]
 1421  1399 Ssl+ tty2     00:00:00 /usr/lib/gdm3/gdm-x-session --run-script twm
 1423  1421 Sl+  tty2     00:00:00 /usr/lib/xorg/Xorg vt2 -displayfd 3 -auth /run/user/1000/gdm/Xauthority -background none -noreset -keeptty -verbose 3
 2225  1690 S+   pts/3    00:00:00 grep --color=auto -i gdm


```

I have another disk, WD5000, with Ubuntu 18.04.3.  I think eog starts right away on that system.

---

### Post by TheFu on 2019-08-27
Below is all useless for this thread. Sorry.

> Could it be that using most Ubuntu DEs will pre-load all the Gnome libraries so that approximately 1GB of libraries doesn't need to be loaded like it would with twm?

Can you check the open files, lsof, on the system before launching whatever program is causing the issues?

I don't have evince, but /usr/bin/atril is a fork and seems to need lots of GTK and Boost libraries.
```
$ ldd   /usr/bin/atril|wc -l
117
```

Those dependencies have to be loaded at some point.

Just a thought.

---

### Post by tomdean@speakeasy.org on 2019-08-27
Bug!

[https://bugs.launchpad.net/ubuntu/+source/eog/+bug/1721401](https://bugs.launchpad.net/ubuntu/+source/eog/+bug/1721401)

---

### Post by tomdean@speakeasy.org on 2019-08-28
The problem is with left-over parts of gnome.  This eliminated the problem:

```

    sudo apt remove --purge gnome-calendar
    sudo apt remove --purge libgnome-todo
    sudo apt remove --purge gnome-mahjongg gnome-mines gnome-sudoku
    sudo apt purge gnome-weather
    sudo apt remove --purge gnome-accessibility-themes gnome-themes-extra:amd64 gnome-themes-extra-data
    sudo apt remove --purge language-pack-gnome-en language-pack-gnome-en-base language-selector-gnome
    sudo apt remove --purge gnome-session-bin gnome-session-canberra gnome-session-common
    sudo apt remove --purge thunderbird-gnome-support pinentry-gnome3 network-manager-pptp-gnome network-manager-gnome
    sudo apt remove --purge libreoffice-gnome libsoup-gnome2.4-1:amd64 nautilus-extension-gnome-terminal policykit-1-gnome
    sudo apt remove --purge libgnome-autoar-0-0:amd64 libgnome-games-support-common libgnome-menu-3-0:amd64 \
             libgnomekbd-common libpam-gnome-keyring:amd64
    sudo apt remove --purge gnome-control-center-data gnome-control-center-faces gnome-desktop3-data gnome-initial-setup
    sudo apt remove --purge gnome-keyring-pkcs11:amd64 gnome-menus gnome-settings-daemon-schemas gnome-video-effects
    sudo apt remove --purge gnome-shell-common gnome-shell-extension-appindicator gnome-shell-extension-ubuntu-dock
    sudo apt remove --purge gnome-software gnome-software-common gnome-terminal-data gnome-todo-common

    The above remove eog
    sudo apt install eog

```
Now, eog image.jpg loads instantly.

---

### Post by TheFu on 2019-08-28
If apt-get is used, you can use file globbing like **sudo apt-get purge gnome***.

I'm rocking fvwm here, but can appreciate anyone who likes the old-school WMs.

---

