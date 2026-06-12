---
title: "running Amarok on GNOME for Libre.fm support"
date: 2009-05-09
forum: General Help
---

### Post by DouglasAWh on 2009-05-09
I've tried both Jaunty and Karmic with similar results.  I am trying to "gobble" to [http://libre.fm](http://libre.fm).  I initially had trouble because I was using python-qt4 instead of python-qt3.  However, now that I have that resolved I am still having issues.  I have kdebase installed.  Now, I'm afraid there is some incompatibilities with the KDE4 base and Amarok 1.4 (where the scripts work).  However, since I have next to zero experience with KDE/Amarok, I don't really know.  Below is the "Output Log".  Any help would be greatly appreciated!

```

/bin/sh: kdialog: not found
Libre.fm gobbler Received notification: playlistChange: cleared

Libre.fm gobbler Received notification: playlistChange: changed

Libre.fm gobbler Received notification: engineStateChange: playing

Libre.fm gobbler Received notification: trackChange

kdialog(5120) KToolInvocation::klauncher: klauncher not running... launching kdeinit
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
kdeinit4: preparing to launch /usr/bin/kded4
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kbuildsycoca4(5128) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/audio/x-sbc.xml" 
kbuildsycoca4(5128) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-ssh-key.xml" 
kbuildsycoca4(5128) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-pem-key.xml" 
kbuildsycoca4(5128) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-hcidump.xml" 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/colorfire.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/helios.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/solarwinds.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/matrixview.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/fieldlines.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/flocks.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/biof.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/sundancer2.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/lattice.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/hyperspace.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/hufo_smoke.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/busyspheres.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/skyrocket.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/lorenz.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/plasma.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/spirographx.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/flux.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/euphoria.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/cyclone.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/hufo_tunnel.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/openoffice.org-startcenter.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/openoffice.org-startcenter.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(5128) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/gcalctool.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kdeinit4: preparing to launch /usr/bin/knotify4
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
Libre.fm gobbler Received notification: trackChange

```

---

