---
title: "mounting home to a separate partition"
date: 2009-03-04
forum: General Help
---

### Post by FraggedLocust on 2009-03-04
I'm trying to mount home to a separate partition using [this method]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") or [this one]("http://www.psychocats.net/ubuntu/separatehome"), but they both give me a ton of errors on the find command.

```
cpio: /mnt/newhome//./wade/.gconf/apps/panel/applets/clock_screen0/prefs: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/applets/clock_screen0/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/applets/clock_screen0: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/applets/fast_user_switch_screen0/prefs/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/applets/fast_user_switch_screen0/prefs: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/applets/fast_user_switch_screen0/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/applets/fast_user_switch_screen0: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/applets/mixer_screen0/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/applets/mixer_screen0: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/applets/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/applets/notification_area_screen0/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/applets/notification_area_screen0: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/applets: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/general/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/general: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/toplevels/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/toplevels/top_panel_screen0/background/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/toplevels/top_panel_screen0/background: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/toplevels/top_panel_screen0/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/toplevels/top_panel_screen0: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/toplevels: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/objects/clock_separator_screen0/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/objects/clock_separator_screen0: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/objects/menu_bar_screen0/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/objects/menu_bar_screen0: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/objects/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel/objects: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/panel: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/nautilus/preferences/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/nautilus/preferences: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/nautilus/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/nautilus/desktop/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/nautilus/desktop: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/nautilus: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/gedit-2/preferences/ui/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/gedit-2/preferences/ui/statusbar/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/gedit-2/preferences/ui/statusbar: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/gedit-2/preferences/ui: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/gedit-2/preferences/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/gedit-2/preferences: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/gedit-2/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/gedit-2: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/metacity/general/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/metacity/general: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/metacity/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/metacity: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/cheese/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/cheese: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/gnome-terminal/profiles/Default: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/gnome-terminal/profiles/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/gnome-terminal/profiles: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/gnome-terminal/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps/gnome-terminal: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/apps: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/system/networking/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/system/networking/connections/1/802-11-wireless/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/system/networking/connections/1/802-11-wireless: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/system/networking/connections/1/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/system/networking/connections/1/connection/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/system/networking/connections/1/connection: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/system/networking/connections/1: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/system/networking/connections/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/system/networking/connections: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/system/networking: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/system/%gconf.xml: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf/system: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconf: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.recently-used.xbel: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.ICEauthority: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.profile: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gtk-bookmarks: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.wapi/shared_fileshare-wade-laptop-Linux-i686-36-11-0: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.wapi/shared_data-wade-laptop-Linux-i686-312-11-0: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.wapi: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gstreamer-0.10/registry.i486.bin: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gstreamer-0.10: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.sudo_as_admin_successful: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gksu.lock: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.dmrc: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Videos/Zack And Miri Make A PornoDvDrip (CanusRG-pill)/Zack And Miri Make A Porno DvDrip (CanusRG-pill).avi: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Videos/Zack And Miri Make A PornoDvDrip (CanusRG-pill)/canus text.txt: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Videos/Zack And Miri Make A PornoDvDrip (CanusRG-pill): Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Videos/Blindness.2008.DvDRip.XviD-FileHunter/Blindness.2008.DvDRip.XviD-FileHunter.avi: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Videos/Blindness.2008.DvDRip.XviD-FileHunter/Blindness-FileHunter.nfo: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Videos/Blindness.2008.DvDRip.XviD-FileHunter: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Videos/Webcam: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Videos/Taken[2008]DvDrip-aXXo/taken-aXXo.nfo: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Videos/Taken[2008]DvDrip-aXXo/Taken[2008]DvDrip-aXXo.avi: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Videos/Taken[2008]DvDrip-aXXo/Demonoid.com.txt: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Videos/Taken[2008]DvDrip-aXXo: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Videos/The.Day.The.Earth.Stood.Still[2008]DvDrip-aXXo/the.day.the.earth.stood.still-aXXo.nfo: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Videos/The.Day.The.Earth.Stood.Still[2008]DvDrip-aXXo/The.Day.The.Earth.Stood.Still[2008]DvDrip-aXXo.avi: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Videos/The.Day.The.Earth.Stood.Still[2008]DvDrip-aXXo/Demonoid.com.txt: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Videos/The.Day.The.Earth.Stood.Still[2008]DvDrip-aXXo: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Videos: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconfd/saved_state: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gconfd: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.compiz/session/1052d55c1d4745590f123608240661539900000125700023: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.compiz/session/1088a786f03b5782ac123616917167838500000057040025: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.compiz/session/1046401b1d45abd66b123614372225693100000063140025: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.compiz/session/10fb181aed76bd797c12360829497301300000057570023: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.compiz/session/10edebf3ba885c328912361021209075700000063400046: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.compiz/session/108b9f27d3bec71a5f12361110827560900000057060024: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.compiz/session/106b1bc8a7a16c579c123613475582585600000073050025: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.compiz/session/105019aacf2ea19da123608638726250300000056440023: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.compiz/session/108da7f1ee4eb8c02123608949141133700000055330023: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.compiz/session: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.compiz: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Desktop: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.update-manager-core/meta-release: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.update-manager-core: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.gvfs: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.bash_history: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.pulse-cookie: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Music: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Documents/Meliae-Dark.tar.gz: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Documents/WinXP.iso: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Documents/LxG_Beta_1.03.tar.gz: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Documents/mythbuntu_8.10_installation.pdf: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Documents/WinXP Key: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Documents: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/amsn_received: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.Xauthority: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.rtorrent.rc~: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.pulse/volume-restore.table: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.pulse: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.fontconfig/61d0ca6f41569ffd9343a4831b06b647-x86.cache-2: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/.fontconfig: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/Webcam/2009-02-13-223502.jpg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/Webcam/2009-02-13-223249.jpg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/Webcam/2009-02-20-213946.jpg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/Webcam/2009-02-20-214043.jpg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/Webcam/2009-02-20-213920.jpg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/Webcam/2009-02-13-223309.jpg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/Webcam/2009-02-20-105600.jpg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/Webcam/2009-02-13-223405.jpg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/Webcam/2009-02-20-214111.jpg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/Webcam/2009-02-20-110855.jpg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/Webcam/2009-02-20-213838.jpg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/Webcam/2009-02-20-214151.jpg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/Webcam/2009-02-20-214232.jpg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/Webcam: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/ubuntu/Hardy.png: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/ubuntu/cube.png: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/ubuntu/Dapper_1.png: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/ubuntu/Dapper_3.png: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/ubuntu/dawn of ubuntu.png: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/ubuntu/Gutsy.png: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/ubuntu/Breezy.png: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/ubuntu/UbuntuVertLogo.svg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/ubuntu/UbuntuLogo.svg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/ubuntu/Ibex_Alternate.png: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/ubuntu/Dapper_2.png: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/ubuntu/UbuntuStrapLogo.svg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/ubuntu/UbuntuLogo2.gif: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/ubuntu/Hoary.png: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/ubuntu/Ubuntu-Wallpaper-1024x786-JDJW.jpg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/ubuntu: Cannot stat: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures/brush-wallpaper.jpg: Cannot open: No such file or directory
cpio: cannot make directory `/mnt/newhome//./wade': Permission denied
cpio: /mnt/newhome//./wade/Pictures: Cannot stat: No such file or directory
cpio: /mnt/newhome//./wade: Cannot stat: Permission denied
0 blocks

```

---

### Post by stchman on 2009-03-04
In the System--->Administration--->Users you can specify where each users home is.  It defaults to /home/<username>, but you can change that.

---

