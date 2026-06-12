---
title: "boot up issue"
date: 2009-05-23
forum: Desktop Environments
---

### Post by riktking on 2009-05-23
hi

really want to try xfce on ubuntu cos i have a rpetty lame laptop. gnome works well, kde is too slow, tried fluxbox etc but they dont quite give enough

installed xfce through

> sudo apt-get install xubuntu-desktop

all ran well, logged out, selected xfce, starts to run then i get:

> Unable to load failsafe session Unable to determine a failsafe session name. Possible causes: xfconfd isn't running (D-Bus setup problem); environment variable $XDG_CONFIG_DIRS is set incorrectly (must include "/etc"), OR xfce4-session is installed incorrectly

ive searched the web with this error and all i can get is an arch linux support thread, which i dont get how to repeat the steps in ubuntu

please can some one help me

thanks

riktking

---

### Post by Macus on 2009-09-24
BUMP

Im getting this too

any idears?

---

### Post by zeroseven0183 on 2009-09-24
Have you tried reinstalling xubuntu-desktop?

---

### Post by Macus on 2009-09-24
yep

tryed that

---

### Post by zeroseven0183 on 2009-09-24
Got this from [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

```
 sudo apt-get remove a2ps abiword abiword-common abiword-help abiword-plugin-grammar abiword-plugin-mathview abiword-plugins app-install-data-commercial aumix catfish cupsys-driver-gutenprint exo-utils fortune-mod fortunes-min gigolo gnumeric gnumeric-common gnumeric-doc gnumeric-gtk gpicview gtk2-engines-xfce imagemagick imagemagick-doc latex-xft-fonts libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libdiscid0 libexo-0.3-0 libfftw3-3 libgda3-3 libgda3-bin libgda3-common libgdl-1-0 libgdl-1-common libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-0-6 libgoffice-0-6-common libgoffice-gtk-0-6 libgsf-gnome-1-114 libgtkmathview0c2a liblink-grammar4 libloudmouth1-0 libmad0 libmpcdec3 libnotify-bin libofa0 libots0 librecode0 libt1-5 libtagc0 libthunar-vfs-1-2 libtunepimp5 libwv-1.2-3 libxfce4menu-0.1-0 libxfce4util4 libxfcegui4-4 libxfconf-0-2 link-grammar-dictionaries-en listen mousepad mozilla-thunderbird orage oss-compat psutils python-gnome2-extras python-musicbrainz2 python-mutagen python-ogg python-pymad python-pyogg python-pysqlite2 python-pyvorbis python-tunepimp scim-modules-table scim-tables-additional tango-icon-theme tango-icon-theme-common tcl8.4 thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird vim-runtime wdiff xchat xchat-common xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-dict-plugin xfce4-fsguard-plugin xfce4-governor-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfswitch-plugin xfwm4 xfwm4-themes xubuntu-artwork xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs 
```

Then reinstall xubuntu-desktop.

Seems it has a broken package/installation.

---

### Post by Macus on 2009-09-24
wait, I was trying the wrong command

but can I do this without downlloading 200mb of stuff?

like its just mythbuntu frontend (pxe booting), it dosent need much

---

### Post by zeroseven0183 on 2009-09-24
I assume you only need **xfce4-session**

---

