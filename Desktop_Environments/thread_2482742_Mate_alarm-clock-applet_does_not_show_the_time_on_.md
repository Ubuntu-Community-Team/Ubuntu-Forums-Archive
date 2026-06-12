---
title: "Mate alarm-clock-applet does not show the time on panel"
date: 2023-01-09
forum: Desktop Environments
---

### Post by attila-mester on 2023-01-09
I managed to install my favorite timer app ([alarm-clock-applet]("https://alarm-clock-applet.github.io/")) on Ubuntu 22.04.01
In Unity it works as I expect, I see the remaining time of the actual alarm besides the app icon:
 [IMG]https://ubuntuforums.org/attachment.php?attachmentid=291553&stc=1[/IMG]


But I'm using Mate (1.26.0) and there it doen't show the time, only the icon:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291554&stc=1[/IMG]

On my old laptop I used 20.04 with Mate and it worked as I like, with the numbers besides the icon on the panel.
I tried several desktop environments (Cinnamon, xfce, enlightenment, etc.) and it was the same, only on Unity works as I prefer -- but I don't like Unity.

(I can check the settings on my old laptop as well, but I don't know what to look for.) Thanks for any advice!

---

### Post by #&amp;thj^% on 2023-01-09
Works better in a Gnome environment,  I think it needs "gnome-control-center", and that would pull in gnome-desktop. EDIT:(Which I'm not suggesting here)
```
apt depends gnome-control-center
gnome-control-center
  Depends: libaccountsservice0 (>= 0.6.40)
  Depends: libadwaita-1-0 (>= 1.2~alpha)
  Depends: libc6 (>= 2.34)
  Depends: libcairo2 (>= 1.2.4)
  Depends: libcolord-gtk4-1 (>= 0.1.24)
  Depends: libcolord2 (>= 1.4.3)
  Depends: libcups2 (>= 1.7.0)
  Depends: libepoxy0 (>= 1.0)
  Depends: libfontconfig1 (>= 2.12.6)
  Depends: libgcr-base-3-1 (>= 3.8.0)
  Depends: libgdk-pixbuf-2.0-0 (>= 2.23.0)
  Depends: libglib2.0-0 (>= 2.70.0)
  Depends: libgnome-bg-4-2 (>= 3.27.90)
  Depends: libgnome-bluetooth-ui-3.0-13 (>= 42~beta)
  Depends: libgnome-desktop-4-2 (>= 3.33.4)
  Depends: libgnome-rr-4-2 (>= 3.17.92)
  Depends: libgnutls30 (>= 3.7.0)
  Depends: libgoa-1.0-0b (>= 3.45)
  Depends: libgoa-backend-1.0-1 (>= 3.45)
  Depends: libgsound0 (>= 1.0.1)
  Depends: libgtk-3-0 (>= 3.21.5)
  Depends: libgtk-4-1 (>= 4.6.0)
  Depends: libgtop-2.0-11 (>= 2.22.3)
  Depends: libgudev-1.0-0 (>= 232)
  Depends: libibus-1.0-5 (>= 1.5.2)
  Depends: libkrb5-3 (>= 1.8+dfsg)
  Depends: libmalcontent-0-0 (>= 0.8.0)
  Depends: libmm-glib0 (>= 1.6.8)
  Depends: libnm0 (>= 1.24.0)
  Depends: libnma-gtk4-0 (>= 1.8.34)
  Depends: libpango-1.0-0 (>= 1.37.2)
  Depends: libpangocairo-1.0-0 (>= 1.14.0)
  Depends: libpolkit-gobject-1-0 (>= 0.103)
  Depends: libpulse-mainloop-glib0 (>= 13.0~)
  Depends: libpulse0 (>= 13.0~)
  Depends: libpwquality1 (>= 1.2.2)
  Depends: libsecret-1-0 (>= 0.7)
  Depends: libsmbclient (>= 2:4.0.3+dfsg1)
  Depends: libsnapd-glib-2-1 (>= 1.63)
  Depends: libudisks2-0 (>= 2.0.0)
  Depends: libupower-glib3 (>= 0.99.8)
  Depends: libwacom9 (>= 2.0.0)
  Depends: libx11-6
  Depends: libxi6 (>= 2:1.2.99.4)
  Depends: libxml2 (>= 2.7.4)
  Depends: accountsservice
  Depends: apg
  Depends: colord (>= 0.1.34)
  Depends: desktop-base (>= 10.0.0)
  Depends: desktop-file-utils
  Depends: gnome-control-center-data (<< 1:44~)
  Depends: gnome-control-center-data (>= 1:43.2-1)
  Depends: gnome-desktop3-data
  Depends: gnome-settings-daemon (>= 41)
  Depends: gsettings-desktop-schemas (>= 42~)
  Depends: webp-pixbuf-loader
  Breaks: gnome-remote-desktop (<< 42)
  Breaks: gnome-shell (<< 42)
  Recommends: cups-pk-helper
  Recommends: gnome-bluetooth-sendto
  Recommends: gnome-online-accounts (>= 3.25.3)
  Recommends: gnome-remote-desktop (>= 42)
  Recommends: gnome-user-docs
  Recommends: gnome-user-share
  Recommends: gkbd-capplet
  Recommends: iso-codes
  Recommends: libcanberra-pulse
  Recommends: polkitd
  Recommends: power-profiles-daemon
 |Recommends: rygel
  Recommends: rygel-tracker
  Recommends: system-config-printer-common (>= 1.4)
  Recommends: malcontent-gui
  Recommends: network-manager-gnome (>= 0.9.8)
  Recommends: libnss-myhostname
  Recommends: cracklib-runtime
  Recommends: pulseaudio-module-bluetooth
  Recommends: realmd
 |Suggests: gnome-software
  Suggests: gnome-packagekit
  Suggests: gstreamer1.0-pulseaudio
  Suggests: pkexec
  Suggests: x11-xserver-utils


```
I have the same results you see in mate and xfce4 but shows in gnome as you show.
Sorry for the bad news.
> Alarm Clock is a fully-featured alarm clock for use with an AppIndicator implementation. 
Sounds vague to me, 
to just satisfy the install all is needed:
```
This program requires the following packages:

cmake >= 3.10
gettext >= 0.19.8
glib-2.0 >= 2.56.4
gtk-3.0 >= 3.22.30
gio-2.0 >= 2.56.4
libnotify >= 0.7.7
gstreamer-1.0 >= 1.14.5
ayatana-appindicator3 >= 0.5.3
gnome-icon-theme
gconf-2.0 >= 3.2.6
pod2man
gzip

```

---

### Post by attila-mester on 2023-01-22
I'm prepared to install whatever needed to have this functionality to see the alarm-clock countdown (the minutes, seconds themselves) on the panel.
I installed gnome-control-center, but still don't know how to make it function.
How can it work in Unity and not in Mate -- when on my other computer (20.04) it worked in Mate as well? Should I check the settings there to get info or with 22.04 something changed so I cannot do it?
Sorry, I'm not that advanced in Linux, but I usually can manage to resolve my issues...

---

### Post by #&amp;thj^% on 2023-01-23
You'll have to take that up with the developer.
```
alarm-clock-applet --version
alarm-clock-applet 0.4.1

```
> How can it work in Unity and not in Mate -
Unity=Gnome Mate=gnome2 fork

---

### Post by ActionParsnip on 2023-01-24
Did you follow this to install the application
[https://alarm-clock-applet.github.io/](https://alarm-clock-applet.github.io/)

If so, I suggest you contact the PPA maintainer

---

