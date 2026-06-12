---
title: "Unity no longer available after upgrade to 14.04"
date: 2014-05-02
forum: Desktop Environments
---

### Post by lads on 2014-05-02
I just upgraded to 14.04, I had no error messages but Unity disappeared from the list of desktop environments in the log in screen. As you can see below, Unity is installed. How can I log in back again with Unity?

```
$ dpkg -l | grep unity
ii  gir1.2-unity-5.0:amd64                      7.1.4+14.04.20140210-0ubuntu1                       amd64        GObject introspection data for the Unity library
ii  gnome-themes-ubuntu                         0.6.1                                               all          Ubuntu community themes
ii  libmeanwhile1                               1.0.2-4.1ubuntu1                                    amd64        open implementation of the Lotus Sametime Community Client protocol
ii  libunity-2d-private0                        7.2.0+14.04.20140423-0ubuntu1.2                     all          transitional dummy package
rc  libunity-action-qt1:amd64                   1.1.0+14.04.20140304-0ubuntu1                       amd64        Unity Action Qt API
ii  libunity-control-center1                    14.04.3+14.04.20140410-0ubuntu1                     amd64        utilities to configure the GNOME desktop
rc  libunity-core-5.0-5                         5.20.0-0ubuntu3                                     amd64        Core library for the Unity interface.
ii  libunity-core-6.0-9                         7.2.0+14.04.20140423-0ubuntu1.2                     amd64        core library for the Unity interface
ii  libunity-gtk2-parser0:amd64                 0.0.0+14.04.20140403-0ubuntu1                       amd64        GtkMenuShell to GMenuModel parser
ii  libunity-gtk3-parser0:amd64                 0.0.0+14.04.20140403-0ubuntu1                       amd64        GtkMenuShell to GMenuModel parser
ii  libunity-misc4                              4.0.5+14.04.20140115-0ubuntu1                       amd64        Miscellaneous functions for Unity - shared library
ii  libunity-protocol-private0:amd64            7.1.4+14.04.20140210-0ubuntu1                       amd64        binding to get places into the launcher - private library
ii  libunity-scopes-json-def-desktop            7.1.4+14.04.20140210-0ubuntu1                       all          binding to get places into the launcher - desktop def file
ii  libunity9:amd64                             7.1.4+14.04.20140210-0ubuntu1                       amd64        binding to get places into the launcher - shared library
ii  libunityvoice1:amd64                        0.1+14.04.20140304-0ubuntu1                         amd64        client library for Unity voice service
ii  unity                                       7.2.0+14.04.20140423-0ubuntu1.2                     amd64        Interface designed for efficiency of space and interaction.
ii  unity-2d                                    7.2.0+14.04.20140423-0ubuntu1.2                     all          transitional dummy package
ii  unity-2d-common                             7.2.0+14.04.20140423-0ubuntu1.2                     all          transitional dummy package
ii  unity-2d-panel                              7.2.0+14.04.20140423-0ubuntu1.2                     all          transitional dummy package
ii  unity-2d-shell                              7.2.0+14.04.20140423-0ubuntu1.2                     all          transitional dummy package
ii  unity-2d-spread                             7.2.0+14.04.20140423-0ubuntu1.2                     all          transitional dummy package
ii  unity-asset-pool                            0.8.24daily13.06.10-0ubuntu1                        all          Unity Assets Pool
rc  unity-common                                5.20.0-0ubuntu3                                     all          Common files for the Unity interface.
ii  unity-control-center                        14.04.3+14.04.20140410-0ubuntu1                     amd64        utilities to configure the GNOME desktop
ii  unity-control-center-signon                 0.1.7~+14.04.20140211.2-0ubuntu4                    amd64        Unity Control Center extension for single signon
ii  unity-greeter                               14.04.9-0ubuntu1                                    amd64        Unity Greeter
ii  unity-gtk-module-common                     0.0.0+14.04.20140403-0ubuntu1                       all          Common files for GtkMenuShell D-Bus exporter
ii  unity-gtk2-module:amd64                     0.0.0+14.04.20140403-0ubuntu1                       amd64        GtkMenuShell D-Bus exporter
ii  unity-gtk3-module:amd64                     0.0.0+14.04.20140403-0ubuntu1                       amd64        GtkMenuShell D-Bus exporter
ii  unity-lens-applications                     7.1.0+13.10.20131011-0ubuntu2                       amd64        Application lens for unity
ii  unity-lens-files                            7.1.0+13.10.20130920-0ubuntu1                       amd64        File lens for unity
ii  unity-lens-friends                          0.1.3+14.04.20140317-0ubuntu1                       amd64        Friends scope for unity
ii  unity-lens-music                            6.9.0+13.10.20131011-0ubuntu1                       amd64        Music lens for unity
ii  unity-lens-photos                           1.0+14.04.20140318-0ubuntu1                         all          Photos lens for Unity
ii  unity-lens-video                            0.3.15+13.10.20130920-0ubuntu1                      amd64        Unity Video lens
ii  unity-scope-audacious                       0.1+13.10.20130927.1-0ubuntu1                       all          Audacious scope for Unity
ii  unity-scope-calculator                      0.1+14.04.20140328-0ubuntu1                         all          Calculator scope for Unity
ii  unity-scope-chromiumbookmarks               0.1+13.10.20130723-0ubuntu1                         all          Chromium bookmarks scope for Unity
ii  unity-scope-clementine                      0.1+13.10.20130723-0ubuntu1                         all          Clementine scope for Unity
ii  unity-scope-colourlovers                    0.1+13.10.20130723-0ubuntu1                         all          COLOURlovers scope for Unity
ii  unity-scope-devhelp                         0.1+14.04.20140328-0ubuntu1                         all          devhelp scope for Unity
ii  unity-scope-firefoxbookmarks                0.1+13.10.20130809.1-0ubuntu1                       all          Firefox bookmarks scope for Unity
ii  unity-scope-gdrive                          0.9+13.10.20130723-0ubuntu1                         all          Google Drive scope for Unity
ii  unity-scope-gmusicbrowser                   0.1+13.10.20130723-0ubuntu1                         all          gmusicbrowser scope for Unity
ii  unity-scope-gourmet                         0.1+13.10.20130723-0ubuntu1                         all          Gourmet Recipe Manager scope for Unity
ii  unity-scope-guayadeque                      0.1+13.10.20130927.1-0ubuntu1                       all          Guayadeque scope for Unity
ii  unity-scope-home                            6.8.2+14.04.20131029.1-0ubuntu1                     amd64        Home scope that aggregates results from multiple scopes
ii  unity-scope-manpages                        3.0+14.04.20140324-0ubuntu1                         all          Manual pages scope for Unity
ii  unity-scope-musicstores                     6.9.0+13.10.20131011-0ubuntu1                       amd64        Ubuntu One music store scope for unity
ii  unity-scope-musique                         0.1+13.10.20130723-0ubuntu1                         all          Musique scope for Unity
ii  unity-scope-openclipart                     0.1+13.10.20130723-0ubuntu1                         all          OpenClipArt scope for Unity
ii  unity-scope-texdoc                          0.1+14.04.20140328-0ubuntu1                         all          Texdoc scope for Unity
ii  unity-scope-tomboy                          0.1+13.10.20130723-0ubuntu1                         all          Tomboy scope for Unity
ii  unity-scope-video-remote                    0.3.15+13.10.20130920-0ubuntu1                      amd64        Remote videos engine
ii  unity-scope-virtualbox                      0.1+13.10.20130723-0ubuntu1                         all          VirtualBox scope for Unity
ii  unity-scope-yelp                            0.1+13.10.20130723-0ubuntu1                         all          Help scope for Unity
ii  unity-scope-zotero                          0.1+13.10.20130723-0ubuntu1                         all          Zotero scope for Unity
ii  unity-scopes-master-default                 6.8.2+14.04.20131029.1-0ubuntu1                     all          Home scope that aggregates results from multiple scopes
ii  unity-scopes-runner                         7.1.4+14.04.20140210-0ubuntu1                       all          desktop runner for misceallenous scopes
ii  unity-services                              7.2.0+14.04.20140423-0ubuntu1.2                     amd64        Services for the Unity interface
ii  unity-settings-daemon                       14.04.0+14.04.20140414-0ubuntu1                     amd64        daemon handling the Unity session settings
ii  unity-voice-service:amd64                   0.1+14.04.20140304-0ubuntu1                         amd64        Voice recognition service for unity
ii  xubuntu-community-wallpapers                14.04.0                                             all          Xubuntu community wallpapers
```

---

### Post by PJs Ronin on 2014-05-02
Try opening a terminal in another DE, or launching TTY1 with Ctrl-Alt-F1 and entering:
```
setsid unity
```

---

### Post by lads on 2014-05-02
> setsid unity

I ran this in a Xubuntu session. A few Unity decorations came up and were overlaid on the Xubuntu elements: panel, dash, etc, creating the weirdest DE I ever seen. The DE became unusable and I had to force a reset.

After reboot the list of available DE in the log in screen is still lacking Unity.

---

### Post by deadflowr on 2014-05-02
```
sudo apt-get install ubuntu-session
```

This will bring the session into the fold.

---

### Post by lads on 2014-05-02
I had to re-install the ubuntu-desktop package:

```
sudo apt-get install --reinstall ubuntu-desktop
```

On a first log in Unity was somewhat freaked out, but after resetting the theme to Ambiance and tweaking the settings back to my preference things got back to normal.

---

