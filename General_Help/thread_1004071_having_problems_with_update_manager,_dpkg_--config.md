---
title: "having problems with update manager, dpkg --configure -a dosn't work."
date: 2008-12-06
forum: General Help
---

### Post by kiddykoff on 2008-12-06
i've been having problems with my update manager. it has told me to run dpkg --configure -a. i've done this but it has not solved all my problems. I've dpkg --audit and this is what it's returned,

The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 gnome-terminal       The GNOME 2 terminal emulator application
 compiz               OpenGL window and compositing manager
 gnome-panel          launcher and docking facility for GNOME
 totem                A simple media player for the GNOME desktop (dummy packag
 totem-gstreamer      A simple media player for the GNOME desktop based on GStr
 totem-mozilla        Totem Mozilla plugin
 gnome-games          games for the GNOME desktop
 gnome-control-center utilities to configure the GNOME desktop
 totem-plugins        Plugins for the Totem media player

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 gnome-settings-daemon GNOME settings daemon
 capplets-data        configuration applets for GNOME 2 - data files
 gedit                official text editor of the GNOME desktop environment
 system-tools-backends System Tools to manage computer configuration -- scripts
 gnome-pilot          A GNOME applet for management of your Palm PDA
 gnome-terminal-data  Data files for the GNOME terminal emulator
 gnome-games-data     data files for the GNOME games
 gnome-panel-data     common files for the GNOME Panel
 totem-common         Data files for the Totem media player
 compiz-gnome         OpenGL window and compositing manager - GNOME window deco
 update-manager       GNOME application that manages apt updates

My brother was telling me that i would have to reinstall my desktop. Is this true? This is the first time using Ubuntu. I've installed Intrepid and have come across this problem after installing ndiswrapper.

Any help would be appreciated. Thanks.

Oh i'm on a gateway mx7118 laptop. if that makes any difference.

---

### Post by adult swim on 2008-12-06
when you ran dpkg --configure -a did you run it as root?
```
sudo dpkg --configure -a
```

---

### Post by kiddykoff on 2008-12-06
yea, i ran it as root, but i didn't figure that out for a while to tell you the truth.

---

### Post by kiddykoff on 2008-12-06
> **adult swim said:**
> when you ran dpkg --configure -a did you run it as root?
```
sudo dpkg --configure -a
```


yea, i ran it as root, but i didn't figure that out for a while to tell you the truth.

---

### Post by adult swim on 2008-12-06
what errors does it say when you run it.

---

### Post by kiddykoff on 2008-12-06
> **adult swim said:**
> what errors does it say when you run it.


```
Setting up gnome-settings-daemon (2.24.0-0ubuntu3.2) ...
**
GConf-Backends:ERROR:markup-tree.c:3378:end_element_handler: assertion failed: (g_slist_length (info->local_schemas) == 1)
dpkg: error processing gnome-settings-daemon (--configure):
 subprocess post-installation script returned error exit status 250
Setting up capplets-data (1:2.24.0.1-0ubuntu7.1) ...
WARNING: Failed to parse default value `??????????? ?????? ;gtk-theme-selector.desktop,???????????? ??????????? ???;default-applications.desktop,??????????? ????;gnome-cups-manager.desktop]' for schema (/schemas/apps/control-center/cc_actions_list)
**
GConf-Backends:ERROR:markup-tree.c:3378:end_element_handler: assertion failed: (g_slist_length (info->local_schemas) == 1)
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 250
Setting up gedit (2.24.1-0ubuntu1) ...
**
GConf-Backends:ERROR:markup-tree.c:3378:end_element_handler: assertion failed: (g_slist_length (info->local_schemas) == 1)
dpkg: error processing gedit (--configure):
 subprocess post-installation script returned error exit status 250
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gnome-pilot (2.0.15-2ubuntu4) ...
**
GConf-Backends:ERROR:markup-tree.c:3378:end_element_handler: assertion failed: (g_slist_length (info->local_schemas) == 1)
dpkg: error processing gnome-pilot (--configure):
 subprocess post-installation script returned error exit status 250
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.24); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.25); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on gnome-settings-daemon; however:
  Package gnome-settings-daemon is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-terminal-data (2.24.1.1-0ubuntu1) ...
**
GConf-Backends:ERROR:markup-tree.c:3378:end_element_handler: assertion failed: (g_slist_length (info->local_schemas) == 1)
dpkg: error processing gnome-terminal-data (--configure):
 subprocess post-installation script returned error exit status 250
Setting up gnome-games-data (1:2.24.1.1-0ubuntu1) ...
**
GConf-Backends:ERROR:markup-tree.c:3378:end_element_handler: assertion failed: (g_slist_length (info->local_schemas) == 1)
dpkg: error processing gnome-games-data (--configure):
 subprocess post-installation script returned error exit status 250
Setting up gnome-panel-data (1:2.24.1-0ubuntu2.1) ...
**
GConf-Backends:ERROR:markup-tree.c:3378:end_element_handler: assertion failed: (g_slist_length (info->local_schemas) == 1)
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 250
Setting up totem-common (2.24.3-0ubuntu1) ...
**
GConf-Backends:ERROR:markup-tree.c:3378:end_element_handler: assertion failed: (g_slist_length (info->local_schemas) == 1)
dpkg: error processing totem-common (--configure):
 subprocess post-installation script returned error exit status 250
Setting up compiz-gnome (1:0.7.8-0ubuntu4.1) ...
**
GConf-Backends:ERROR:markup-tree.c:3378:end_element_handler: assertion failed: (g_slist_length (info->local_schemas) == 1)
dpkg: error processing compiz-gnome (--configure):
 subprocess post-installation script returned error exit status 250
dpkg: dependency problems prevent configuration of compiz:
 compiz depends on compiz-gnome; however:
  Package compiz-gnome is not configured yet.
dpkg: error processing compiz (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-gstreamer:
 totem-gstreamer depends on totem-common (>= 2.24); however:
  Package totem-common is not configured yet.
 totem-gstreamer depends on totem-common (<< 2.25); however:
  Package totem-common is not configured yet.
dpkg: error processing totem-gstreamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-mozilla:
 totem-mozilla depends on totem-gstreamer (>= 2.24.3-0ubuntu1) | totem-xine (>= 2.24.3-0ubuntu1); however:
  Package totem-gstreamer is not configured yet.
  Package totem-xine is not installed.
dpkg: error processing totem-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-games:
 gnome-games depends on gnome-games-data (>= 1:2.24); however:
  Package gnome-games-data is not configured yet.
 gnome-games depends on gnome-games-data (<< 1:2.25); however:
  Package gnome-games-data is not configured yet.
dpkg: error processing gnome-games (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-plugins:
 totem-plugins depends on totem-gstreamer (= 2.24.3-0ubuntu1) | totem-xine (= 2.24.3-0ubuntu1); however:
  Package totem-gstreamer is not configured yet.
  Package totem-xine is not installed.
dpkg: error processing totem-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem:
 totem depends on totem-plugins (>= 2.24.3-0ubuntu1); however:
  Package totem-plugins is not configured yet.
 totem depends on totem-gstreamer (>= 2.24.3-0ubuntu1) | totem-xine (>= 2.24.3-0ubuntu1); however:
  Package totem-gstreamer is not configured yet.
  Package totem-xine is not installed.
dpkg: error processing totem (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-settings-daemon
 capplets-data
 gedit
 system-tools-backends
 gnome-pilot
 gnome-control-center
 gnome-terminal-data
 gnome-games-data
 gnome-panel-data
 totem-common
 compiz-gnome
 compiz
 totem-gstreamer
 totem-mozilla
 gnome-games
 totem-plugins
 totem

```

---

### Post by kiddykoff on 2008-12-06
i'm going to bed, i'll be back tomorrow.

---

### Post by adult swim on 2008-12-07
those are some pretty wild errors, ive never seen them before (thats not saying much.)  did you change anything else before you installed ndiswrapper?  did you follow any guides when you installed ndiswrapper?

---

### Post by kiddykoff on 2008-12-07
> **adult swim said:**
> those are some pretty wild errors, ive never seen them before (thats not saying much.)  did you change anything else before you installed ndiswrapper?  did you follow any guides when you installed ndiswrapper?

i installed ndsigtk and that's all. I don't recall doing anything else.

---

### Post by kiddykoff on 2008-12-07
oh i do remember uninstalling some bluetooth packages through the synaptic manager. I have reinstalled those though.

---

### Post by kiddykoff on 2008-12-10
bump

---

### Post by kiddykoff on 2008-12-12
any help would be appreciated.

bump

---

