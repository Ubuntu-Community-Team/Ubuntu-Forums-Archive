---
title: "xset dpms force off does not work"
date: 2014-06-07
forum: Desktop Environments
---

### Post by leptogenesis2 on 2014-06-07
I'm trying to blank the screen in xfce on xubuntu 14.04.  The standard approach I've always used is "xset dpms force off", but here it doesn't seem to work.  One of two things happens: either the screen goes off and comes back on in about 1 second, or it goes black for about 5 seconds and then I'm back at the login screen (when I login, all my windows are still there).  How can I turn off the screen in xubuntu?

---

### Post by grumblebum2 on 2014-06-07
In a terminal try running ...
```
sleep 1 && xset dpms force off
```

---

### Post by leptogenesis2 on 2014-06-08
Ah, so I guess the first case was just the xset command activating before I'd let up the return key.  Funny, I never saw this when launching the xset command from the unity launcher.  I guess xfce is faster after all.

But the second case now occurs reliably--i.e. i'm back to the login screen.  This is what shows up in the syslog:

[FONT=courier new][FONT=courier new]Jun  7 20:59:50 my-laptop acpid: client 1880[0:0] has disconnected
Jun  7 20:59:50 my-laptop acpid: client connected from 8899[0:0]
Jun  7 20:59:50 my-laptop acpid: 1 client rule loaded
Jun  7 20:59:51 my-laptop dbus[1365]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jun  7 20:59:51 my-laptop dbus[1365]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jun  7 20:59:51 my-laptop colord: Device added: xrandr-Lenovo Group Limited
Jun  7 20:59:51 my-laptop colord: Profile added: icc-7f612c50506bb2a30560867fb37e58cf
Jun  7 20:59:51 my-laptop colord: Profile added: icc-cf38c84d5e415d74f98baa8ab18d8f42
Jun  7 20:59:51 my-laptop colord: Automatic metadata add icc-752daadca9962e022e984b81c954aa88 to xrandr-Lenovo Group Limited
Jun  7 20:59:51 my-laptop colord: Profile added: icc-752daadca9962e022e984b81c954aa88
Jun  7 20:59:56 my-laptop colord: device removed: xrandr-Lenovo Group Limited
Jun  7 20:59:56 my-laptop colord: Profile removed: icc-7f612c50506bb2a30560867fb37e58cf
Jun  7 20:59:56 my-laptop colord: Profile removed: icc-cf38c84d5e415d74f98baa8ab18d8f42
Jun  7 20:59:56 my-laptop colord: Profile removed: icc-752daadca9962e022e984b81c954aa88
[/FONT][/FONT]

---

### Post by leptogenesis2 on 2014-06-08
More info--it seems this isn't xubuntu specific; I reproduced the problem in unity.  Then I completely uninstalled everything I installed to get xubuntu-desktop, i.e. all of the following packages:

[FONT=courier new]desktop-base gnumeric libxfce4util-bin brltty-x11 libxfce4ui-2-0 mugshot xfce4-power-manager-data gmusicbrowser plymouth-theme-xubuntu-logo xfce4-verve-plugin xscreensaver-data libabiword-3.0 libchamplain-gtk-0.12-0 menulibre abiword xubuntu-desktop xbrlapi libexo-1-0 orage xfce4-power-manager gnumeric-common xfce4-netload-plugin python3-psutil xfce4-whiskermenu-plugin xfce4-systemload-plugin libxfce4ui-common xfce4-volumed xfce4-mailwatch-plugin libgstreamer-perl libxfce4ui-1-0 thunar-archive-plugin xfce4-session xscreensaver lightdm-gtk-greeter libkeybinder0 xfce4-places-plugin libtumbler-1-0 libexo-common abiword-plugin-grammar xubuntu-artwork libotr5 xfconf libots0 libxfce4ui-utils xfburn thunar-media-tags-plugin xfce4-xkb-plugin xfce4-quicklauncher-plugin gtk-theme-config gnome-themes-standard-data libsexy2 libxfconf-0-2 plymouth-theme-xubuntu-text abiword-plugin-mathview xfce4-indicator-plugin blueman catfish parole python-psutil gnumeric-doc pidgin-otr apt-offline libjpeg-progs thunar-data libgarcon-common ristretto xfce4-appfinder pastebinit light-locker xubuntu-community-wallpapers xfdesktop4-data libintl-perl xfce4-settings xfce4-screenshooter xfce4-cpugraph-plugin abiword-common libxfce4util-common libwv-1.2-4 libgdome2-0 libgoffice-0.10-10-common xubuntu-default-settings libgtk2-notify-perl tumbler-common xchat-common libgsf-1-common libxfcegui4-4 xubuntu-docs thunar-volman xchat-indicator libgarcon-1-0 xfce4-notes libexo-helpers liblink-grammar4 libgsf-1-114 exo-utils shimmer-themes python3-pexpect libdigest-crc-perl libjpeg-turbo-progs libgoffice-0.10-10 mousepad libthunarx-2-0 xfwm4 xfce4-notes-plugin tumbler xfce4-weather-plugin xfce4-dict libchamplain-0.12-0 xfdesktop4 libgdome2-cpp-smart0c2a xubuntu-icon-theme xfce4-panel xfce4-terminal xfce4-notifyd thunar libgtk2-trayicon-perl libgtkmathview0c2a xchat link-grammar-dictionaries-en xubuntu-wallpapers gnome-themes-standard libxfce4util6 gigolo light-locker-settings libtagc0 xfce4-taskmanager[/FONT]

and the problem went away on ubuntu.  My guess is that desktop-base is actually using some "clever" mechanism to detect that the user is no longer using one particular desktop environment, and automatically gives the user the opportunity to switch.  xset dpms force off somehow triggers this mechanism, which sends you back to the login screen, which then turns the screen back on.

Could somebody else could try installing a second DE and see if this issue is reproducible? If so, I'll file a bug.

---

