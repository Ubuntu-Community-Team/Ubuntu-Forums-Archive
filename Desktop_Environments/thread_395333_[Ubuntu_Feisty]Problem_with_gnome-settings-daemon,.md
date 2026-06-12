---
title: "[Ubuntu Feisty]Problem with gnome-settings-daemon, it &quot;does not start&quot;"
date: 2007-03-28
forum: Desktop Environments
---

### Post by Joe_Bishop on 2007-03-28
When I try to launch "keyboard preferences" I get a window with the message:
> Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
And when keyboard settings applet appears, but when I change any setting, I get:
> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70200000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

and:
> master@master:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us,ru", ",winkeys", "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us,ru", ",winkeys", "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"

master@master:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [en,ru       winkeys]
 model = pc105
 options = [lv3 lv3:ralt_switch,grp     grp:ctrl_shift_toggle,altwin    altwin:super_win]
 overrideSettings = true

---

### Post by Joe_Bishop on 2007-03-28
I did not install any setting manager from others DE and WM

---

### Post by ashunter on 2007-03-28
I have got a big problem with Ubuntu after i update the kernel to 2.6.20-13
Codecs::~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
fast-user-switch-applet gnome2-user-guide
The following NEW packages will be installed:
 mscompress setserial wacom-tools
The following packages will be upgraded: 
avahi-autoipd avahi-daemon brltty brltty-x11 cupsys-driver-gutenprint  firefox 
firefox-gnome-support foo2zjs foomatic-db-hpijs foomatic-filters  gimp-print 
gnome-panel gnome-panel-data gnome-power-manager libavahi-client3  libavahi-
common-data libavahi-common3 libavahi-core5 libavahi-glib1  libbrlapi1 
libcairo2 libgutenprint2 libgutenprintui2-1 libnspr4 libnss3 libpanel-applet2
-0 libtotem-plparser1 python-central  python-software-properties software-
properties-gtk totem totem-gstreamer  totem-mozilla xserver-xorg-input-wacom 
xserver-xorg-video-ati  xserver-xorg-video-nv
36 upgraded, 3 newly installed, 2 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/33.7MB of archives.After unpacking 18.1MB disk space will be 
freed.Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 94155 files and directories currently installed.)
Removing fast-user-switch-applet ...
Segmentation fault
dpkg: error processing fast-user-switch-applet (--remove):
 subprocess post-removal script returned error exit status 139
Removing gnome2-user-guide ...
Segmentation fault
dpkg: error processing gnome2-user-guide (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 fast-user-switch-applet
 gnome2-user-guide
E: Sub-process /usr/bin/dpkg returned an error code (1)

Now i can't install or remove any software.And my gdm doesn't work correct ,i have to "startx" to get in the desktop environment.
I have done like this :sudo apt-get install -f 
dpkg --force-all  --purge gnome2-user-guide
and even sudo apt-get --purge remove liborbit2
None of them works...
I use the main server source.Who can help me?Thanks

---

