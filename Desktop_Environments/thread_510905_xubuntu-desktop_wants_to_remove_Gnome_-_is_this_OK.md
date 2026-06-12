---
title: "xubuntu-desktop wants to remove Gnome - is this OK, or as bad as it sounds?"
date: 2007-07-27
forum: Desktop Environments
---

### Post by OzzyFrank on 2007-07-27
Hiya. I'm wanting to install "xubuntu-desktop" so I can have Xfce/Xubuntu in addition to my Gnome/Ubuntu and KDE/Kubuntu. However, unlike when I added KDE via the Kubuntu Alternate CD, I am being told "gnome" and "gnome-desktop-environment" need to be removed. Are these "metapackages" that are just a list of things to install at once, and so can be removed (like "ubuntu-desktop") without incident, or is the install really wanting to get rid of Gnome? I just thought I better make sure of this before proceeding. Thanks.

---

### Post by pbcartwright on 2007-07-27
try just installing xfce, I have xfce,KDE and gnome all installed happily :)
here are the xfce packages I have installed:

libxfce4util-4.4.1-3.1
xfce4-panel-plugin-places-0.3.0-22.1
xfce4-panel-plugin-mount-0.5.1-22.1
xfce4-panel-plugin-smartpm-0.1.2-22.1
xfce4-session-4.4.1-24.1
xfce4-panel-plugin-screenshooter-1.0.0-22.1
xfce4-dev-tools-4.4.0-9.1
libxfce4mcs-4.4.1-5.1
xfce-mcs-manager-4.4.1-14.2
xfce-mcs-plugins-4.4.1-16.2
pyxfce-4.4.0-6.2
xfce4-panel-plugin-notes-1.4.1-22.1
xfce4-panel-plugin-sensors-0.10.0-22.1
notification-daemon-xfce-0.3.7-12.1
xfce4-taskmanager-0.4.0_rc2-16.1
xfce4-panel-4.4.1-10.2
xfce4-volstatus-0.1.0-7.2
xfce4-mixer-4.4.1-15.2
xfce4-panel-plugin-quicklauncher-1.9.4-22.1
xfce4-panel-plugin-smartbookmark-0.4.2-22.1
xfce4-panel-plugin-radio-0.2.0-22.1
xfce4-appfinder-4.4.1-14.3
libxfcegui4-4.4.1-8.1
xfce4-panel-plugin-mpc-0.3.2-22.1
xfce4-panel-plugin-weather-0.6.0-22.1
xfce4-desktop-4.4.1-32.2

---

### Post by merlinus on 2007-07-27
```

sudo aptitude update && sudo aptitude install xubuntu-desktop

```

-merlin

---

### Post by aysiu on 2007-07-27
Those are, in fact, metapackages. To be safe, do this: ```
sudo aptitude update && sudo aptitude install xubuntu-desktop && sudo aptitude install ubuntu-desktop
```

---

### Post by OzzyFrank on 2007-07-27
Hiya. Thanks for your help, y'all. I sort of went with the first suggestion, but just did a search for "xfce" in Synaptic, and just went through the list grabbing what I wanted (knowing that anything that was actually needed would be installed). The last tip with reinstalling ubuntu-desktop at the same time is good and I've made a note of that for other things that may pop up like this.

Anyway, installed Xfce and included the Xubuntu settings package/file, and all seems well and just the same as an actual Xubuntu install on the old PC in the lounge. Still like to know why it wanted to remove those (and other) gnome packages, when kubuntu-desktop wasn't as hard to please. Out of curiosity, if someone knows the answer for this, I'd like to know. Cheers. Frank

---

