---
title: "Gnome System Monitor crashes on startup."
date: 2009-08-01
forum: Desktop Environments
---

### Post by Intrepid Ibex on 2009-08-01
When I open Gnome System Monitor, I almost instantly I get the bug report pop-up window with this log:
```
Distribution: Unknown
Gnome Release: 2.26.3 2009-07-03 (Archlinux)
BugBuddy Version: 2.26.0

System: Linux 2.6.30-ARCH #1 SMP PREEMPT Fri Jul 31 18:10:38 UTC 2009 i686
X Vendor: The X.Org Foundation
X Vendor Release: 10602000
Selinux: No
Accessibility: Disabled
GTK+ Theme: Wii-Black
Icon Theme: Royal Blue
GTK+ Modules: canberra-gtk-module, gnomebreakpad

Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0



----------- .xsession-errors (6882 sec old) ---------------------
amarok(7690)/kio (KDirListerCache) KDirListerCache::listDir: Listing directory: KUrl("file:///home/det")
amarok(7690)/libplasma Plasma::ViewPrivate::updateSceneRect: !!!!!!!!!!!!!!!!! setting the scene rect to QRectF(0,0 50x50) associated screen is -1
amarok(7690)/kio (KDirListerCache) KDirListerCache::listDir: Entry currently being listed: KUrl("trash:/") by (KDirLister(0x8c18d80) )
amarok(7690)/kio (Slave) KIO::Slave::createSlave: createSlave "trash" for KUrl("trash:/")
amarok(7690)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-det/amarokSa7690.slave-socket"
klauncher(7547)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-detVF0ko8/ksycoca4"
klauncher(7547)/kio (KLauncher) KLauncher::requestSlave: KLauncher: launching new slave  "kio_trash"  with protocol= "trash"  args= ("trash", "local:/tmp/ksocket-det/klauncherMT7547.slave-socket", "lo
kdeinit4: Got EXEC_NEW 'kio_trash' from launcher.
kdeinit4: preparing to launch 
klauncher(7547)/kio (KLauncher) KLauncher::processRequestReturn: "kio_trash" (pid 7702) up and running.
amarok(7690)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///home/det")
amarok(7690)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-det/amaroksc7690.slave-socket"
klauncher(7547)/kio (KLauncher) KLauncher::requestSlave: KLauncher: launching new slave  "kio_file"  with protocol= "file"  args= ("file", "local:/tmp/ksocket-det/klauncherMT7547.slave-socket", "local
kdeinit4: 
...Too much output, ignoring rest...
--------------------------------------------------

```

Complete reinstalling of gnome-system-monitor doesn't help, however changing the theme from custom gnome-look.org to original themes does o.O.

Here's the whole .xsession-errors if someone wants to read:
```
/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: ssh-agent not found!
/etc/gdm/Xsession: Setup done, will execute: gnome-session
gnome-session[7271]: WARNING: Could not parse desktop file /home/det/.config/autostart/xfconf-migration-4.6.desktop: Key file does not have key 'Name'
gnome-session[7271]: WARNING: could not read /home/det/.config/autostart/xfconf-migration-4.6.desktop
GNOME_KEYRING_SOCKET=/tmp/keyring-yaYgOg/socket
SSH_AUTH_SOCK=/tmp/keyring-yaYgOg/socket.ssh
Window manager warning: "" found in configuration database is not a valid value for keybinding "activate_window_menu"
Window manager warning: Failed to read saved session file /home/det/.config/metacity/sessions/1081f2d4addd5eab99124917117637128500000072710022.ms: Failed to open file '/home/det/.config/metacity/sessions/1081f2d4addd5eab99124917117637128500000072710022.ms': No such file or directory

MCS->Xfconf settings migration complete

polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
konqueror(7420) kdemain: Unknown class  ""  in session saved data! 
** Message: Initializing gksu extension...
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
 * Detected Session: gnome
 * Searching for installed applications...
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
/usr/lib/python2.6/site-packages/FusionIcon/interface_gtk/main.py:214: GtkWarning: gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
  gtk.main()

** (nautilus:7417): WARNING **: Unable to add monitor: Not supported
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
konqueror(7420)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-detVF0ko8/ksycoca4"
konqueror(7420)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///home/det/.kde4/share/apps/konqueror/autosave/owned_by_1.25")
konqueror(7420)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-det/konquerorZT7420.slave-socket"
konqueror(7420) KToolInvocation::klauncher: klauncher not running... launching kdeinit
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
klauncher(7547)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-det/klauncherMT7547.slave-socket"
kdeinit4: Launched KLauncher, pid = 7547 result = 0
kdeinit4: opened connection to :0.0
kdeinit4: preparing to launch /usr/bin/kded4
kdeinit4: Launched KDED, pid = 7548 result = 0
kdeinit4: Got EXT_EXEC '/usr/bin/kbuildsycoca4' from launcher.
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
klauncher(7547)/kio (KLauncher) KLauncher::processRequestReturn: "/usr/bin/kbuildsycoca4" (pid 7550) up and running.
kbuildsycoca4 running...
kbuildsycoca4(7550)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-detVF0ko8/ksycoca4"
kbuildsycoca4(7550) KBuildSycoca::checkTimestamps: checking file timestamps
kbuildsycoca4(7550) KBuildSycoca::checkDirTimestamps: timestamp changed: "/home/det/.config/menus/settings.menu"
kbuildsycoca4(7550) kdemain: Reusing existing ksycoca
kbuildsycoca4(7550) KBuildSycoca::recreate: Recreating ksycoca file ("/var/tmp/kdecache-detVF0ko8/ksycoca4", version 131)
kbuildsycoca4(7550) KBuildSycoca::createEntry: new: "screensaver.desktop"
kbuildsycoca4(7550) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/home/det/.config/menus/kde-applications-merged/cxmenu-cxoffice-0.menu"
kbuildsycoca4(7550) VFolderMenu::pushDocInfo: Menu "applications-kmenuedit.menu" not found.
kbuildsycoca4(7550) VFolderMenu::processMenu: Processing KDE Legacy dirs for <KDE>
kbuildsycoca4(7550) VFolderMenu::processKDELegacyDirs:
kbuildsycoca4(7550) VFolderMenu::loadApplications: Looking up applications under "/usr/share/gdm/applications/"
kbuildsycoca4(7550) VFolderMenu::loadApplications: Looking up applications under "/opt/kde/share/applications/"
kbuildsycoca4(7550) VFolderMenu::loadApplications: Looking up applications under "/opt/kde/share/applications/kde/"
kbuildsycoca4(7550) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/"
kbuildsycoca4(7550) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/screensavers/"
kbuildsycoca4(7550) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/supertuxkart.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7550) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/gcalctool.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7550) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/thunderbird3.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7550) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/banshee-1.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7550) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/gdesklets.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7550) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/kde4/"
kbuildsycoca4(7550)/kdecore (KService) KServicePrivate::init: The desktop entry file  "/usr/share/applications/kde4/koffice.desktop"  has Type= "Application"  but no Exec line 

kbuildsycoca4(7550)/kdecore (KService) KBuildServiceFactory::createEntry: Invalid Service :  "/usr/share/applications/kde4/koffice.desktop" 
kbuildsycoca4(7550) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/enemy-territory.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7550) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/firefox.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7550) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/"
kbuildsycoca4(7550) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/"
kbuildsycoca4(7550) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/"
kbuildsycoca4(7550) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Mono 2.4.2.1 for Windows/"
kbuildsycoca4(7550) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Mono 2.4.2.1 for Windows/Applications/"
kbuildsycoca4(7550) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Mono 2.4.2.1 for Windows/XSP/"
kbuildsycoca4(7550) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Notepad++/"
kbuildsycoca4(7550) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Steam/"
kbuildsycoca4(7550) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Steam/Uninstall/"
kbuildsycoca4(7550) VFolderMenu::loadApplications: Looking up applications under "/home/det/.cxoffice/desktopdata/cxoffice-0/cxmenu/xdg-kde-applications/CrossOver/"
kbuildsycoca4(7550) VFolderMenu::processMenu: Menu "#Hidden" does not specify a directory file.
kbuildsycoca4(7550) VFolderMenu::processCondition: Adding file "Install+Windows+Software.desktop"
kbuildsycoca4(7550) VFolderMenu::processCondition: Adding file "Configuration.desktop"
kbuildsycoca4(7550) VFolderMenu::processCondition: Adding file "Documentation.desktop"
kbuildsycoca4(7550) VFolderMenu::processCondition: Adding file "Terminate+Windows+Applications.desktop"
kbuildsycoca4(7550) VFolderMenu::processCondition: Adding file "Run+a+Windows+Command.desktop"
kbuildsycoca4(7550) VFolderMenu::processCondition: Adding file "Uninstall.desktop"
kbuildsycoca4(7550) VFolderMenu::processCondition: Adding file "kde-kcm_knetworkconfmodule_ss.desktop"
kbuildsycoca4(7550) VFolderMenu::processCondition: Adding file "kde-medianotifications.desktop"
kbuildsycoca4(7550) VFolderMenu::processCondition: Adding file "kde-audioencoding.desktop"
kbuildsycoca4(7550) KBuildMimeTypeFactory::parseSubclassFile: Now parsing "/home/det/.local/share/mime/subclasses"
kbuildsycoca4(7550) KBuildMimeTypeFactory::parseSubclassFile: Now parsing "/usr/share/mime/subclasses"
kbuildsycoca4(7550) KBuildMimeTypeFactory::parseAliasFile: Now parsing "/home/det/.local/share/mime/aliases"
kbuildsycoca4(7550) KBuildMimeTypeFactory::parseAliasFile: Now parsing "/usr/share/mime/aliases"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/jpg"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/x-gray"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/x-png"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/Document Viewer.desktop" specifies undefined mimetype/servicetype "image/*"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/subtitleeditor.desktop" specifies undefined mimetype/servicetype "application/x-microdvd"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/subtitleeditor.desktop" specifies undefined mimetype/servicetype "application/x-subviewer"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/avidemux.desktop" specifies undefined mimetype/servicetype "application/x-extension-mp4"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/avidemux.desktop" specifies undefined mimetype/servicetype "application/x-extension-m4a"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/avidemux.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/amarok_append.desktop" specifies undefined mimetype/servicetype "audio/*"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.spreadsheetml.template"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.template.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.binary.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/gimp.desktop" specifies undefined mimetype/servicetype "image/pcx"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.presentation.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Impress.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.presentationml.template"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.template.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-base.desktop" specifies undefined mimetype/servicetype "application/vnd.sun.xml.base"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/10-rootactionsfolders.desktop" specifies undefined mimetype/servicetype "inode/directory-locked"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-writer.desktop" specifies undefined mimetype/servicetype "application/x-doc"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.document.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-writer.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.wordprocessingml.template"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.template.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-xcf-gimp"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-targa"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-xbm"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-xpm"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-vnd.adobe.photoshop"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-7z-compressed-tar"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-ar"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-bzip1"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-bzip1-compressed-tar"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-cabinet"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-ear"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-lzop-compressed-tar"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-rar-compressed"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-rzip"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-war"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "multipart/x-zip"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Writer.desktop" specifies undefined mimetype/servicetype "application/x-doc"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.document.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Writer.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.wordprocessingml.template"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.template.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.presentation.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-impress.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.presentationml.template"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.template.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/msvideo"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/x-flc"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-ms-asf"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-ms-wax"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-real-audio"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "misc/ultravox"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "application/x-extension-mp4"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "text/x-abiword"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "text/x-xml-abiword"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "application/vnd.plain"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "application/x-crossmark"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "application/wordperfect6"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "application/wordperfect5.1"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/nautilus-folder-handler.desktop" specifies undefined mimetype/servicetype "x-directory/gnome-default-handler"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Base.desktop" specifies undefined mimetype/servicetype "application/vnd.sun.xml.base"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/pcmanfm-folder-handler.desktop" specifies undefined mimetype/servicetype "x-directory/gnome-default-handler"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/acroread.desktop" specifies undefined mimetype/servicetype "application/vnd.fdf"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/acroread.desktop" specifies undefined mimetype/servicetype "application/vnd.adobe.pdx"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/acroread.desktop" specifies undefined mimetype/servicetype "application/vnd.adobe.xdp+xml"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/acroread.desktop" specifies undefined mimetype/servicetype "application/vnd.adobe.xfdf"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/x-quicktime"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/mkv"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/msvideo"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/aiff"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-realaudio"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-basic"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-8svx"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/8svx"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-16sv"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/168sv"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "image/ilbm"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/anim"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "image/x-png"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/mng"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-real-audio"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/mpeg2"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg2"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg3"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "x-mpegurl"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/musepack"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/musepack"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-ape"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/ape"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-musepack"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-id3"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg-3"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/mpc"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/x-mpc"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/mp"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/x-mp"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/flac"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.presentation.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/impress.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.presentationml.template"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.template.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-cdrao-toc"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-nrg"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-mds"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-daa"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-cif"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-b6t"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-c2d"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-cdi"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-ccd"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/x-musepack"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/musepack"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/musepack"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/x-ape"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/ape"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/x-id3"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg-3"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audip/mp3"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/mpc"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/x-mpc"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/mp"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/x-mp"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/flac"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/writer.desktop" specifies undefined mimetype/servicetype "application/x-doc"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.document.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/writer.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.wordprocessingml.template"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.template.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/base.desktop" specifies undefined mimetype/servicetype "application/vnd.sun.xml.base"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/musepack"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-ape"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-democracy"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-extension-m4a"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-extension-mp4"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-id3"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-miro"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-musepack"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-troff-msvideo"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/ape"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/avi"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/flac"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/mp"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/mp4a-latm"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/mpc"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/musepack"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/wave"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-mp"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-mpc"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg-3"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-ms-asf"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-ms-wax"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-sbc"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "image/avi"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "misc/ultravox"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "video/msvideo"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "video/x-flc"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "video/x-mpg"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/calc.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.spreadsheetml.template"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.template.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.binary.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/evince.desktop" specifies undefined mimetype/servicetype "image/*"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/amarok.desktop" specifies undefined mimetype/servicetype "application/x-ogm-audio"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/brasero-open-image.desktop" specifies undefined mimetype/servicetype "application/x-toc"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/shaman.desktop" specifies undefined mimetype/servicetype "application/x-shaman-package"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Calc.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.spreadsheetml.template"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.template.macroenabled.12"
kbuildsycoca4(7550) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.binary.macroenabled.12"
kbuildsycoca4(7550) KMimeAssociations::parseAllMimeAppsList: Parsing "/home/det/.local/share/applications/mimeapps.list"
kbuildsycoca4(7550) KMimeAssociations::parseAddedAssociations: "/home/det/.local/share/applications/mimeapps.list" specifies unknown service "kde4-kmplayer.desktop" in "Added Associations"
kbuildsycoca4(7550) KMimeFileParser::parseGlobFiles: Now parsing "/usr/share/mime/globs2"
kbuildsycoca4(7550) KMimeFileParser::parseGlobFiles: Now parsing "/home/det/.local/share/mime/globs2"
kdeinit4: PID 7550 terminated.
kdeinit4: Got EXT_EXEC '/usr/bin/kbuildsycoca4' from launcher.
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
klauncher(7547)/kio (KLauncher) KLauncher::processRequestReturn: "/usr/bin/kbuildsycoca4" (pid 7551) up and running.
kbuildsycoca4 running...
kbuildsycoca4(7551)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-detVF0ko8/ksycoca4"
kbuildsycoca4(7551) kdemain: Reusing existing ksycoca
kbuildsycoca4(7551) KBuildSycoca::recreate: Recreating ksycoca file ("/var/tmp/kdecache-detVF0ko8/ksycoca4", version 131)
kbuildsycoca4(7551) KBuildSycoca::createEntry: new: "screensaver.desktop"
kbuildsycoca4(7551) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/home/det/.config/menus/kde-applications-merged/cxmenu-cxoffice-0.menu"
kbuildsycoca4(7551) VFolderMenu::pushDocInfo: Menu "applications-kmenuedit.menu" not found.
kbuildsycoca4(7551) VFolderMenu::processMenu: Processing KDE Legacy dirs for <KDE>
kbuildsycoca4(7551) VFolderMenu::processKDELegacyDirs:
kbuildsycoca4(7551) VFolderMenu::loadApplications: Looking up applications under "/usr/share/gdm/applications/"
kbuildsycoca4(7551) VFolderMenu::loadApplications: Looking up applications under "/opt/kde/share/applications/"
kbuildsycoca4(7551) VFolderMenu::loadApplications: Looking up applications under "/opt/kde/share/applications/kde/"
kbuildsycoca4(7551) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/"
kbuildsycoca4(7551) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/screensavers/"
kbuildsycoca4(7551) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/supertuxkart.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7551) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/gcalctool.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7551) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/thunderbird3.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7551) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/banshee-1.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7551) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/gdesklets.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7551) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/kde4/"
kbuildsycoca4(7551)/kdecore (KService) KServicePrivate::init: The desktop entry file  "/usr/share/applications/kde4/koffice.desktop"  has Type= "Application"  but no Exec line 

kbuildsycoca4(7551)/kdecore (KService) KBuildServiceFactory::createEntry: Invalid Service :  "/usr/share/applications/kde4/koffice.desktop" 
kbuildsycoca4(7551) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/enemy-territory.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7551) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/firefox.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7551) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/"
kbuildsycoca4(7551) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/"
kbuildsycoca4(7551) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/"
kbuildsycoca4(7551) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Mono 2.4.2.1 for Windows/"
kbuildsycoca4(7551) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Mono 2.4.2.1 for Windows/Applications/"
kbuildsycoca4(7551) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Mono 2.4.2.1 for Windows/XSP/"
kbuildsycoca4(7551) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Notepad++/"
kbuildsycoca4(7551) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Steam/"
kbuildsycoca4(7551) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Steam/Uninstall/"
kbuildsycoca4(7551) VFolderMenu::loadApplications: Looking up applications under "/home/det/.cxoffice/desktopdata/cxoffice-0/cxmenu/xdg-kde-applications/CrossOver/"
kbuildsycoca4(7551) VFolderMenu::processMenu: Menu "#Hidden" does not specify a directory file.
kbuildsycoca4(7551) VFolderMenu::processCondition: Adding file "Install+Windows+Software.desktop"
kbuildsycoca4(7551) VFolderMenu::processCondition: Adding file "Configuration.desktop"
kbuildsycoca4(7551) VFolderMenu::processCondition: Adding file "Documentation.desktop"
kbuildsycoca4(7551) VFolderMenu::processCondition: Adding file "Terminate+Windows+Applications.desktop"
kbuildsycoca4(7551) VFolderMenu::processCondition: Adding file "Run+a+Windows+Command.desktop"
kbuildsycoca4(7551) VFolderMenu::processCondition: Adding file "Uninstall.desktop"
kbuildsycoca4(7551) VFolderMenu::processCondition: Adding file "kde-kcm_knetworkconfmodule_ss.desktop"
kbuildsycoca4(7551) VFolderMenu::processCondition: Adding file "kde-medianotifications.desktop"
kbuildsycoca4(7551) VFolderMenu::processCondition: Adding file "kde-audioencoding.desktop"
kbuildsycoca4(7551) KBuildMimeTypeFactory::parseSubclassFile: Now parsing "/home/det/.local/share/mime/subclasses"
kbuildsycoca4(7551) KBuildMimeTypeFactory::parseSubclassFile: Now parsing "/usr/share/mime/subclasses"
kbuildsycoca4(7551) KBuildMimeTypeFactory::parseAliasFile: Now parsing "/home/det/.local/share/mime/aliases"
kbuildsycoca4(7551) KBuildMimeTypeFactory::parseAliasFile: Now parsing "/usr/share/mime/aliases"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/jpg"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/x-gray"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/x-png"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/Document Viewer.desktop" specifies undefined mimetype/servicetype "image/*"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/subtitleeditor.desktop" specifies undefined mimetype/servicetype "application/x-microdvd"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/subtitleeditor.desktop" specifies undefined mimetype/servicetype "application/x-subviewer"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/avidemux.desktop" specifies undefined mimetype/servicetype "application/x-extension-mp4"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/avidemux.desktop" specifies undefined mimetype/servicetype "application/x-extension-m4a"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/avidemux.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/amarok_append.desktop" specifies undefined mimetype/servicetype "audio/*"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.spreadsheetml.template"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.template.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.binary.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/gimp.desktop" specifies undefined mimetype/servicetype "image/pcx"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.presentation.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Impress.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.presentationml.template"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.template.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-base.desktop" specifies undefined mimetype/servicetype "application/vnd.sun.xml.base"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/10-rootactionsfolders.desktop" specifies undefined mimetype/servicetype "inode/directory-locked"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-writer.desktop" specifies undefined mimetype/servicetype "application/x-doc"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.document.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-writer.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.wordprocessingml.template"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.template.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-xcf-gimp"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-targa"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-xbm"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-xpm"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-vnd.adobe.photoshop"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-7z-compressed-tar"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-ar"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-bzip1"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-bzip1-compressed-tar"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-cabinet"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-ear"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-lzop-compressed-tar"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-rar-compressed"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-rzip"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-war"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "multipart/x-zip"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Writer.desktop" specifies undefined mimetype/servicetype "application/x-doc"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.document.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Writer.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.wordprocessingml.template"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.template.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.presentation.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-impress.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.presentationml.template"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.template.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/msvideo"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/x-flc"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-ms-asf"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-ms-wax"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-real-audio"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "misc/ultravox"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "application/x-extension-mp4"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "text/x-abiword"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "text/x-xml-abiword"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "application/vnd.plain"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "application/x-crossmark"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "application/wordperfect6"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "application/wordperfect5.1"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/nautilus-folder-handler.desktop" specifies undefined mimetype/servicetype "x-directory/gnome-default-handler"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Base.desktop" specifies undefined mimetype/servicetype "application/vnd.sun.xml.base"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/pcmanfm-folder-handler.desktop" specifies undefined mimetype/servicetype "x-directory/gnome-default-handler"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/acroread.desktop" specifies undefined mimetype/servicetype "application/vnd.fdf"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/acroread.desktop" specifies undefined mimetype/servicetype "application/vnd.adobe.pdx"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/acroread.desktop" specifies undefined mimetype/servicetype "application/vnd.adobe.xdp+xml"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/acroread.desktop" specifies undefined mimetype/servicetype "application/vnd.adobe.xfdf"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/x-quicktime"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/mkv"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/msvideo"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/aiff"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-realaudio"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-basic"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-8svx"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/8svx"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-16sv"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/168sv"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "image/ilbm"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/anim"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "image/x-png"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/mng"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-real-audio"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/mpeg2"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg2"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg3"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "x-mpegurl"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/musepack"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/musepack"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-ape"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/ape"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-musepack"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-id3"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg-3"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/mpc"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/x-mpc"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/mp"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/x-mp"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/flac"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.presentation.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/impress.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.presentationml.template"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.template.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-cdrao-toc"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-nrg"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-mds"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-daa"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-cif"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-b6t"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-c2d"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-cdi"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-ccd"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/x-musepack"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/musepack"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/musepack"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/x-ape"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/ape"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/x-id3"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg-3"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audip/mp3"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/mpc"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/x-mpc"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/mp"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/x-mp"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/flac"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/writer.desktop" specifies undefined mimetype/servicetype "application/x-doc"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.document.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/writer.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.wordprocessingml.template"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.template.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/base.desktop" specifies undefined mimetype/servicetype "application/vnd.sun.xml.base"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/musepack"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-ape"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-democracy"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-extension-m4a"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-extension-mp4"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-id3"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-miro"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-musepack"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-troff-msvideo"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/ape"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/avi"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/flac"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/mp"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/mp4a-latm"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/mpc"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/musepack"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/wave"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-mp"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-mpc"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg-3"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-ms-asf"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-ms-wax"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-sbc"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "image/avi"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "misc/ultravox"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "video/msvideo"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "video/x-flc"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "video/x-mpg"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/calc.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.spreadsheetml.template"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.template.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.binary.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/evince.desktop" specifies undefined mimetype/servicetype "image/*"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/amarok.desktop" specifies undefined mimetype/servicetype "application/x-ogm-audio"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/brasero-open-image.desktop" specifies undefined mimetype/servicetype "application/x-toc"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/shaman.desktop" specifies undefined mimetype/servicetype "application/x-shaman-package"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Calc.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.spreadsheetml.template"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.template.macroenabled.12"
kbuildsycoca4(7551) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.binary.macroenabled.12"
kbuildsycoca4(7551) KMimeAssociations::parseAllMimeAppsList: Parsing "/home/det/.local/share/applications/mimeapps.list"
kbuildsycoca4(7551) KMimeAssociations::parseAddedAssociations: "/home/det/.local/share/applications/mimeapps.list" specifies unknown service "kde4-kmplayer.desktop" in "Added Associations"
kbuildsycoca4(7551) KMimeFileParser::parseGlobFiles: Now parsing "/usr/share/mime/globs2"
kbuildsycoca4(7551) KMimeFileParser::parseGlobFiles: Now parsing "/home/det/.local/share/mime/globs2"
kdeinit4: PID 7551 terminated.
kded(7549)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-detVF0ko8/ksycoca4"
kded(7549)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-detVF0ko8/ksycoca4"
klauncher(7547)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-detVF0ko8/ksycoca4"
kdeinit4: Got EXEC_NEW 'kconf_update' from launcher.
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
klauncher(7547)/kio (KLauncher) KLauncher::processRequestReturn: "kconf_update" (pid 7552) up and running.
kdeinit4: PID 7552 terminated.
kdeinit4: PID 7548 terminated.
klauncher(7547)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-detVF0ko8/ksycoca4"
klauncher(7547)/kio (KLauncher) KLauncher::requestSlave: KLauncher: launching new slave  "kio_file"  with protocol= "file"  args= ("file", "local:/tmp/ksocket-det/klauncherMT7547.slave-socket", "local:/tmp/ksocket-det/konquerorZT7420.slave-socket")
kdeinit4: Got EXEC_NEW 'kio_file' from launcher.
kdeinit4: preparing to launch 
klauncher(7547)/kio (KLauncher) KLauncher::processRequestReturn: "kio_file" (pid 7553) up and running.
kio_file(7553) kdemain: Starting  7553
kio_file(7553) FileProtocol::stat: FileProtocol::stat details= 0
konqueror(7420)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-detVF0ko8/ksycoca4"
kio_file(7553) FileProtocol::listDir: ========= LIST  "file:///home/det/.kde4/share/apps/konqueror/autosave/owned_by_1.25"  =========
kio_file(7553) FileProtocol::listDir: ============= COMPLETED LIST ============
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
kdeinit4: Got EXT_EXEC '/usr/bin/kbuildsycoca4' from launcher.
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
<unknown program name>(7546)/ KStartupInfo::createNewStartupId: creating:  "myhost;1249171200;468642;7546_TIME0" : "unnamed app"
klauncher(7547)/kio (KLauncher) KLauncher::processRequestReturn: "/usr/bin/kbuildsycoca4" (pid 7559) up and running.
kbuildsycoca4 running...
kbuildsycoca4(7559)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-detVF0ko8/ksycoca4"
kbuildsycoca4(7559) kdemain: Reusing existing ksycoca
kbuildsycoca4(7559) KBuildSycoca::recreate: Recreating ksycoca file ("/var/tmp/kdecache-detVF0ko8/ksycoca4", version 131)
kbuildsycoca4(7559) KBuildSycoca::createEntry: new: "screensaver.desktop"
kbuildsycoca4(7559) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/home/det/.config/menus/kde-applications-merged/cxmenu-cxoffice-0.menu"
kbuildsycoca4(7559) VFolderMenu::pushDocInfo: Menu "applications-kmenuedit.menu" not found.
kbuildsycoca4(7559) VFolderMenu::processMenu: Processing KDE Legacy dirs for <KDE>
kbuildsycoca4(7559) VFolderMenu::processKDELegacyDirs:
kbuildsycoca4(7559) VFolderMenu::loadApplications: Looking up applications under "/usr/share/gdm/applications/"
kbuildsycoca4(7559) VFolderMenu::loadApplications: Looking up applications under "/opt/kde/share/applications/"
kbuildsycoca4(7559) VFolderMenu::loadApplications: Looking up applications under "/opt/kde/share/applications/kde/"
kbuildsycoca4(7559) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/"
kbuildsycoca4(7559) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/screensavers/"
kbuildsycoca4(7559) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/supertuxkart.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7559) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/gcalctool.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7559) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/thunderbird3.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7559) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/banshee-1.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7559) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/gdesklets.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7559) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/kde4/"
kbuildsycoca4(7559)/kdecore (KService) KServicePrivate::init: The desktop entry file  "/usr/share/applications/kde4/koffice.desktop"  has Type= "Application"  but no Exec line 

kbuildsycoca4(7559)/kdecore (KService) KBuildServiceFactory::createEntry: Invalid Service :  "/usr/share/applications/kde4/koffice.desktop" 
kbuildsycoca4(7559) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/enemy-territory.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7559) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/firefox.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7559) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/"
kbuildsycoca4(7559) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/"
kbuildsycoca4(7559) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/"
kbuildsycoca4(7559) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Mono 2.4.2.1 for Windows/"
kbuildsycoca4(7559) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Mono 2.4.2.1 for Windows/Applications/"
kbuildsycoca4(7559) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Mono 2.4.2.1 for Windows/XSP/"
kbuildsycoca4(7559) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Notepad++/"
kbuildsycoca4(7559) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Steam/"
kbuildsycoca4(7559) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Steam/Uninstall/"
kbuildsycoca4(7559) VFolderMenu::loadApplications: Looking up applications under "/home/det/.cxoffice/desktopdata/cxoffice-0/cxmenu/xdg-kde-applications/CrossOver/"
kbuildsycoca4(7559) VFolderMenu::processMenu: Menu "#Hidden" does not specify a directory file.
kbuildsycoca4(7559) VFolderMenu::processCondition: Adding file "Install+Windows+Software.desktop"
kbuildsycoca4(7559) VFolderMenu::processCondition: Adding file "Configuration.desktop"
kbuildsycoca4(7559) VFolderMenu::processCondition: Adding file "Documentation.desktop"
kbuildsycoca4(7559) VFolderMenu::processCondition: Adding file "Terminate+Windows+Applications.desktop"
kbuildsycoca4(7559) VFolderMenu::processCondition: Adding file "Run+a+Windows+Command.desktop"
kbuildsycoca4(7559) VFolderMenu::processCondition: Adding file "Uninstall.desktop"
kbuildsycoca4(7559) VFolderMenu::processCondition: Adding file "kde-kcm_knetworkconfmodule_ss.desktop"
kbuildsycoca4(7559) VFolderMenu::processCondition: Adding file "kde-medianotifications.desktop"
kbuildsycoca4(7559) VFolderMenu::processCondition: Adding file "kde-audioencoding.desktop"
kbuildsycoca4(7559) KBuildMimeTypeFactory::parseSubclassFile: Now parsing "/home/det/.local/share/mime/subclasses"
kbuildsycoca4(7559) KBuildMimeTypeFactory::parseSubclassFile: Now parsing "/usr/share/mime/subclasses"
kbuildsycoca4(7559) KBuildMimeTypeFactory::parseAliasFile: Now parsing "/home/det/.local/share/mime/aliases"
kbuildsycoca4(7559) KBuildMimeTypeFactory::parseAliasFile: Now parsing "/usr/share/mime/aliases"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/jpg"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/x-gray"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/x-png"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/Document Viewer.desktop" specifies undefined mimetype/servicetype "image/*"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/subtitleeditor.desktop" specifies undefined mimetype/servicetype "application/x-microdvd"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/subtitleeditor.desktop" specifies undefined mimetype/servicetype "application/x-subviewer"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/avidemux.desktop" specifies undefined mimetype/servicetype "application/x-extension-mp4"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/avidemux.desktop" specifies undefined mimetype/servicetype "application/x-extension-m4a"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/avidemux.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/amarok_append.desktop" specifies undefined mimetype/servicetype "audio/*"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.spreadsheetml.template"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.template.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.binary.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/gimp.desktop" specifies undefined mimetype/servicetype "image/pcx"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.presentation.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Impress.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.presentationml.template"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.template.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-base.desktop" specifies undefined mimetype/servicetype "application/vnd.sun.xml.base"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/10-rootactionsfolders.desktop" specifies undefined mimetype/servicetype "inode/directory-locked"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-writer.desktop" specifies undefined mimetype/servicetype "application/x-doc"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.document.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-writer.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.wordprocessingml.template"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.template.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-xcf-gimp"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-targa"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-xbm"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-xpm"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-vnd.adobe.photoshop"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-7z-compressed-tar"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-ar"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-bzip1"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-bzip1-compressed-tar"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-cabinet"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-ear"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-lzop-compressed-tar"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-rar-compressed"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-rzip"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-war"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "multipart/x-zip"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Writer.desktop" specifies undefined mimetype/servicetype "application/x-doc"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.document.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Writer.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.wordprocessingml.template"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.template.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.presentation.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-impress.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.presentationml.template"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.template.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/msvideo"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/x-flc"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-ms-asf"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-ms-wax"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-real-audio"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "misc/ultravox"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "application/x-extension-mp4"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "text/x-abiword"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "text/x-xml-abiword"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "application/vnd.plain"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "application/x-crossmark"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "application/wordperfect6"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "application/wordperfect5.1"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/nautilus-folder-handler.desktop" specifies undefined mimetype/servicetype "x-directory/gnome-default-handler"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Base.desktop" specifies undefined mimetype/servicetype "application/vnd.sun.xml.base"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/pcmanfm-folder-handler.desktop" specifies undefined mimetype/servicetype "x-directory/gnome-default-handler"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/acroread.desktop" specifies undefined mimetype/servicetype "application/vnd.fdf"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/acroread.desktop" specifies undefined mimetype/servicetype "application/vnd.adobe.pdx"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/acroread.desktop" specifies undefined mimetype/servicetype "application/vnd.adobe.xdp+xml"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/acroread.desktop" specifies undefined mimetype/servicetype "application/vnd.adobe.xfdf"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/x-quicktime"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/mkv"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/msvideo"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/aiff"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-realaudio"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-basic"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-8svx"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/8svx"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-16sv"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/168sv"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "image/ilbm"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/anim"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "image/x-png"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/mng"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-real-audio"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/mpeg2"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg2"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg3"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "x-mpegurl"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/musepack"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/musepack"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-ape"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/ape"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-musepack"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-id3"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg-3"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/mpc"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/x-mpc"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/mp"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/x-mp"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/flac"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.presentation.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/impress.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.presentationml.template"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.template.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-cdrao-toc"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-nrg"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-mds"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-daa"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-cif"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-b6t"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-c2d"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-cdi"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-ccd"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/x-musepack"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/musepack"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/musepack"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/x-ape"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/ape"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/x-id3"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg-3"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audip/mp3"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/mpc"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/x-mpc"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/mp"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/x-mp"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/flac"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/writer.desktop" specifies undefined mimetype/servicetype "application/x-doc"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.document.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/writer.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.wordprocessingml.template"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.template.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/base.desktop" specifies undefined mimetype/servicetype "application/vnd.sun.xml.base"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/musepack"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-ape"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-democracy"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-extension-m4a"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-extension-mp4"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-id3"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-miro"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-musepack"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-troff-msvideo"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/ape"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/avi"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/flac"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/mp"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/mp4a-latm"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/mpc"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/musepack"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/wave"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-mp"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-mpc"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg-3"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-ms-asf"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-ms-wax"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-sbc"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "image/avi"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "misc/ultravox"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "video/msvideo"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "video/x-flc"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "video/x-mpg"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/calc.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.spreadsheetml.template"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.template.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.binary.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/evince.desktop" specifies undefined mimetype/servicetype "image/*"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/amarok.desktop" specifies undefined mimetype/servicetype "application/x-ogm-audio"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/brasero-open-image.desktop" specifies undefined mimetype/servicetype "application/x-toc"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/shaman.desktop" specifies undefined mimetype/servicetype "application/x-shaman-package"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Calc.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.spreadsheetml.template"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.template.macroenabled.12"
kbuildsycoca4(7559) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.binary.macroenabled.12"
kbuildsycoca4(7559) KMimeAssociations::parseAllMimeAppsList: Parsing "/home/det/.local/share/applications/mimeapps.list"
kbuildsycoca4(7559) KMimeAssociations::parseAddedAssociations: "/home/det/.local/share/applications/mimeapps.list" specifies unknown service "kde4-kmplayer.desktop" in "Added Associations"
kbuildsycoca4(7559) KMimeFileParser::parseGlobFiles: Now parsing "/usr/share/mime/globs2"
kbuildsycoca4(7559) KMimeFileParser::parseGlobFiles: Now parsing "/home/det/.local/share/mime/globs2"
kdeinit4: PID 7559 terminated.
kded(7549)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-detVF0ko8/ksycoca4"
VLC media player 1.0.1 Goldeneye
[0x8616990] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

** (<unknown>:7561): WARNING **: Invalid borders specified for theme pixmap:
        /home/det/.themes/Wii-Black/gtk-2.0/Range/trough-horizontal.png,
borders don't fit within the image
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1

(metacity-dialog:7581): Gdk-CRITICAL **: gdk_x11_atom_to_xatom_for_display: assertion `atom != GDK_NONE' failed
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
fixme:wbemprox:wbem_locator_ConnectServer 0x1ab7f8, L"ROOT\\CIMV2", (null), (null), (null), 0x00000080, (null), (nil), 0x348d3e8)
fixme:wbemprox:DllCanUnloadNow 
fixme:shdocvw:ViewObject_SetAdvise (0x1af450)->(1 00000002 0x15fe908)
fixme:shdocvw:PersistStreamInit_InitNew (0x1af450)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1af450)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1af450)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1afa00)->(1 00000002 0x15fe9a8)
fixme:shdocvw:PersistStreamInit_InitNew (0x1afa00)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1afa00)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1afa00)->(ffffffff)
fixme:win:RegisterDeviceNotificationA (hwnd=0x10092, filter=0x32de50,flags=0x00000004),
	returns a fake device notification handle!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x32c188,0x00000000), stub!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x1ca8f0)->(1 00000002 0x1de14a8)
fixme:shdocvw:PersistStreamInit_InitNew (0x1ca8f0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1ca8f0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1ca8f0)->(ffffffff)
fixme:vxd:VXD_Open Unknown/unsupported VxD L"gdperf.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1ca8f0)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1ca8f0)
fixme:shdocvw:OleObject_Close (0x1ca8f0)->(1)
fixme:win:EnumDisplayDevicesW ((null),0,0x33e0bc,0x00000000), stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x161838, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33e58c)
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:vxd:VXD_Open Unknown/unsupported VxD L"gdperf.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e2b0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x10137600) : pBox=0x33e304 stub
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:shdocvw:ViewObject_SetAdvise (0x104c22c8)->(1 00000002 0xd52698)
fixme:shdocvw:PersistStreamInit_InitNew (0x104c22c8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x104c22c8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x104c22c8)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x10576698)->(1 00000002 0xd521a8)
fixme:shdocvw:PersistStreamInit_InitNew (0x10576698)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10576698)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10576698)->(ffffffff)
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:d3d_surface:surface_load_ds_location (0x180550) Not supported with fixed up depth stencil
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x104da2b0) : pBox=0x33e378 stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x10661c20,0x106a3648): stub
err:ntdll:RtlpWaitForCriticalSection section 0xbf75a4 "?" wait timed out in thread 001e, blocked by 001f, retrying (60 sec)
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
err:ntdll:RtlpWaitForCriticalSection section 0xbf75a4 "?" wait timed out in thread 001e, blocked by 001f, retrying (60 sec)
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
polkit-read-auth-helper: needs to be setgid policykit
kdeinit4: Got EXT_EXEC '/usr/bin/kbuildsycoca4' from launcher.
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
<unknown program name>(7546)/ KStartupInfo::createNewStartupId: creating:  "myhost;1249171310;927388;7546_TIME0" : "unnamed app"
kbuildsycoca4 running...
kbuildsycoca4(7687)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-detVF0ko8/ksycoca4"
kbuildsycoca4(7687) kdemain: Reusing existing ksycoca
klauncher(7547)/kio (KLauncher) KLauncher::processRequestReturn: "/usr/bin/kbuildsycoca4" (pid 7687) up and running.
kbuildsycoca4(7687) KBuildSycoca::recreate: Recreating ksycoca file ("/var/tmp/kdecache-detVF0ko8/ksycoca4", version 131)
kbuildsycoca4(7687) KBuildSycoca::createEntry: new: "screensaver.desktop"
kbuildsycoca4(7687) VFolderMenu::mergeFile: VFolderMenu::mergeFile: "/home/det/.config/menus/kde-applications-merged/cxmenu-cxoffice-0.menu"
kbuildsycoca4(7687) VFolderMenu::pushDocInfo: Menu "applications-kmenuedit.menu" not found.
kbuildsycoca4(7687) VFolderMenu::processMenu: Processing KDE Legacy dirs for <KDE>
kbuildsycoca4(7687) VFolderMenu::processKDELegacyDirs:
kbuildsycoca4(7687) VFolderMenu::loadApplications: Looking up applications under "/usr/share/gdm/applications/"
kbuildsycoca4(7687) VFolderMenu::loadApplications: Looking up applications under "/opt/kde/share/applications/"
kbuildsycoca4(7687) VFolderMenu::loadApplications: Looking up applications under "/opt/kde/share/applications/kde/"
kbuildsycoca4(7687) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/"
kbuildsycoca4(7687) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/screensavers/"
kbuildsycoca4(7687) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/supertuxkart.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7687) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/gcalctool.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7687) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/thunderbird3.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7687) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/banshee-1.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7687) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/gdesklets.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7687) VFolderMenu::loadApplications: Looking up applications under "/usr/share/applications/kde4/"
kbuildsycoca4(7687)/kdecore (KService) KServicePrivate::init: The desktop entry file  "/usr/share/applications/kde4/koffice.desktop"  has Type= "Application"  but no Exec line 

kbuildsycoca4(7687)/kdecore (KService) KBuildServiceFactory::createEntry: Invalid Service :  "/usr/share/applications/kde4/koffice.desktop" 
kbuildsycoca4(7687) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/enemy-territory.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7687) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/firefox.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7687) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/"
kbuildsycoca4(7687) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/"
kbuildsycoca4(7687) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/"
kbuildsycoca4(7687) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Mono 2.4.2.1 for Windows/"
kbuildsycoca4(7687) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Mono 2.4.2.1 for Windows/Applications/"
kbuildsycoca4(7687) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Mono 2.4.2.1 for Windows/XSP/"
kbuildsycoca4(7687) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Notepad++/"
kbuildsycoca4(7687) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Steam/"
kbuildsycoca4(7687) VFolderMenu::loadApplications: Looking up applications under "/home/det/.local/share/applications/wine/Programs/Steam/Uninstall/"
kbuildsycoca4(7687) KBuildSycoca::createEntry: modified: "/home/det/.local/share/applications/acroread.desktop"
kbuildsycoca4(7687) KBuildSycoca::createEntry: new: "/home/det/.local/share/applications/impress.desktop"
kbuildsycoca4(7687) KBuildSycoca::createEntry: new: "/home/det/.local/share/applications/writer.desktop"
kbuildsycoca4(7687) VFolderMenu::loadApplications: Looking up applications under "/home/det/.cxoffice/desktopdata/cxoffice-0/cxmenu/xdg-kde-applications/CrossOver/"
kbuildsycoca4(7687) VFolderMenu::processMenu: Menu "#Hidden" does not specify a directory file.
kbuildsycoca4(7687) VFolderMenu::processCondition: Adding file "Install+Windows+Software.desktop"
kbuildsycoca4(7687) VFolderMenu::processCondition: Adding file "Configuration.desktop"
kbuildsycoca4(7687) VFolderMenu::processCondition: Adding file "Documentation.desktop"
kbuildsycoca4(7687) VFolderMenu::processCondition: Adding file "Terminate+Windows+Applications.desktop"
kbuildsycoca4(7687) VFolderMenu::processCondition: Adding file "Run+a+Windows+Command.desktop"
kbuildsycoca4(7687) VFolderMenu::processCondition: Adding file "Uninstall.desktop"
kbuildsycoca4(7687) VFolderMenu::processCondition: Adding file "kde-kcm_knetworkconfmodule_ss.desktop"
kbuildsycoca4(7687) VFolderMenu::processCondition: Adding file "kde-medianotifications.desktop"
kbuildsycoca4(7687) VFolderMenu::processCondition: Adding file "kde-audioencoding.desktop"
kbuildsycoca4(7687) KBuildMimeTypeFactory::parseSubclassFile: Now parsing "/home/det/.local/share/mime/subclasses"
kbuildsycoca4(7687) KBuildMimeTypeFactory::parseSubclassFile: Now parsing "/usr/share/mime/subclasses"
kbuildsycoca4(7687) KBuildMimeTypeFactory::parseAliasFile: Now parsing "/home/det/.local/share/mime/aliases"
kbuildsycoca4(7687) KBuildMimeTypeFactory::parseAliasFile: Now parsing "/usr/share/mime/aliases"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/jpg"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/x-gray"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/eog.desktop" specifies undefined mimetype/servicetype "image/x-png"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/Document Viewer.desktop" specifies undefined mimetype/servicetype "image/*"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/subtitleeditor.desktop" specifies undefined mimetype/servicetype "application/x-microdvd"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/subtitleeditor.desktop" specifies undefined mimetype/servicetype "application/x-subviewer"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/avidemux.desktop" specifies undefined mimetype/servicetype "application/x-extension-mp4"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/avidemux.desktop" specifies undefined mimetype/servicetype "application/x-extension-m4a"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/avidemux.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/amarok_append.desktop" specifies undefined mimetype/servicetype "audio/*"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.spreadsheetml.template"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.template.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.binary.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/gimp.desktop" specifies undefined mimetype/servicetype "image/pcx"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.presentation.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Impress.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.presentationml.template"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.template.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-base.desktop" specifies undefined mimetype/servicetype "application/vnd.sun.xml.base"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/10-rootactionsfolders.desktop" specifies undefined mimetype/servicetype "inode/directory-locked"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-writer.desktop" specifies undefined mimetype/servicetype "application/x-doc"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.document.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-writer.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.wordprocessingml.template"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.template.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-xcf-gimp"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-targa"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-xbm"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-xpm"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/krita_magick.desktop" specifies undefined mimetype/servicetype "image/x-vnd.adobe.photoshop"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-7z-compressed-tar"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-ar"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-bzip1"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-bzip1-compressed-tar"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-cabinet"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-ear"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-lzop-compressed-tar"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-rar-compressed"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-rzip"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "application/x-war"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/file-roller.desktop" specifies undefined mimetype/servicetype "multipart/x-zip"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Writer.desktop" specifies undefined mimetype/servicetype "application/x-doc"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.document.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Writer.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.wordprocessingml.template"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.template.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.presentation.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-impress.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.presentationml.template"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/Beta-impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.template.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/msvideo"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "video/x-flc"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-ms-asf"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-ms-wax"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-real-audio"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "misc/ultravox"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/vlc.desktop" specifies undefined mimetype/servicetype "application/x-extension-mp4"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "text/x-abiword"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "text/x-xml-abiword"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "application/vnd.plain"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "application/x-crossmark"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "application/wordperfect6"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/abiword.desktop" specifies undefined mimetype/servicetype "application/wordperfect5.1"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/nautilus-folder-handler.desktop" specifies undefined mimetype/servicetype "x-directory/gnome-default-handler"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Base.desktop" specifies undefined mimetype/servicetype "application/vnd.sun.xml.base"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/pcmanfm-folder-handler.desktop" specifies undefined mimetype/servicetype "x-directory/gnome-default-handler"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/acroread.desktop" specifies undefined mimetype/servicetype "application/vnd.fdf"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/acroread.desktop" specifies undefined mimetype/servicetype "application/vnd.adobe.pdx"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/acroread.desktop" specifies undefined mimetype/servicetype "application/vnd.adobe.xdp+xml"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/acroread.desktop" specifies undefined mimetype/servicetype "application/vnd.adobe.xfdf"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/x-quicktime"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/mkv"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/msvideo"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/aiff"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-realaudio"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-basic"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-8svx"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/8svx"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-16sv"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/168sv"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "image/ilbm"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/anim"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "image/x-png"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/mng"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-real-audio"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/mpeg2"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg2"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg3"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "phononbackends/xine.desktop" specifies undefined mimetype/servicetype "x-mpegurl"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/musepack"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/musepack"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-ape"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/ape"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-musepack"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-id3"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg-3"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/mpc"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/x-mpc"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/mp"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/x-mp"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/exaile.desktop" specifies undefined mimetype/servicetype "audio/flac"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.presentation.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/impress.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.presentationml.template"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/impress.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-powerpoint.template.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-cdrao-toc"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-nrg"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-mds"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-daa"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-cif"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-b6t"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-c2d"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-cdi"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "ServiceMenus/kde_cdemu_mount.desktop" specifies undefined mimetype/servicetype "application/x-ccd"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/x-musepack"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/musepack"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/musepack"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/x-ape"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/ape"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/x-id3"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg-3"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audip/mp3"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/mpc"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/x-mpc"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/mp"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/x-mp"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/listen.desktop" specifies undefined mimetype/servicetype "audio/flac"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/writer.desktop" specifies undefined mimetype/servicetype "application/x-doc"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.document.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/writer.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.wordprocessingml.template"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/writer.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-word.template.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/base.desktop" specifies undefined mimetype/servicetype "application/vnd.sun.xml.base"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/musepack"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-ape"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-democracy"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-extension-m4a"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-extension-mp4"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-flac"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-id3"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-miro"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-musepack"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "application/x-troff-msvideo"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/ape"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/avi"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/flac"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/mp"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/mp4a-latm"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/mpc"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/mpeg3"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/musepack"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/wave"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-mp"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-mpc"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-mpeg-3"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-ms-asf"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-ms-wax"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-pn-aiff"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-pn-au"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-pn-wav"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-pn-windows-acm"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "audio/x-sbc"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "image/avi"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "misc/ultravox"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "video/msvideo"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "video/x-flc"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "video/x-mpeg"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/banshee-1.desktop" specifies undefined mimetype/servicetype "video/x-mpg"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/calc.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.spreadsheetml.template"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.template.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.binary.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/evince.desktop" specifies undefined mimetype/servicetype "image/*"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/kde4/amarok.desktop" specifies undefined mimetype/servicetype "application/x-ogm-audio"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/brasero-open-image.desktop" specifies undefined mimetype/servicetype "application/x-toc"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/usr/share/applications/shaman.desktop" specifies undefined mimetype/servicetype "application/x-shaman-package"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Calc.desktop" specifies undefined mimetype/servicetype "application/vnd.openxmlformats-officedocument.spreadsheetml.template"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.template.macroenabled.12"
kbuildsycoca4(7687) KBuildServiceFactory::populateServiceTypes: "/home/det/.local/share/applications/OpenOffice.org beta Calc.desktop" specifies undefined mimetype/servicetype "application/vnd.ms-excel.sheet.binary.macroenabled.12"
kbuildsycoca4(7687) KMimeAssociations::parseAllMimeAppsList: Parsing "/home/det/.local/share/applications/mimeapps.list"
kbuildsycoca4(7687) KMimeAssociations::parseAddedAssociations: "/home/det/.local/share/applications/mimeapps.list" specifies unknown service "kde4-kmplayer.desktop" in "Added Associations"
kbuildsycoca4(7687) KMimeFileParser::parseGlobFiles: Now parsing "/usr/share/mime/globs2"
kbuildsycoca4(7687) KMimeFileParser::parseGlobFiles: Now parsing "/home/det/.local/share/mime/globs2"
kdeinit4: PID 7687 terminated.
kded(7549)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-detVF0ko8/ksycoca4"
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x4c00004 specified for 0x4c00064 (amarok).
kded(7549)/phonon (kded module) PS::AudioDevice::applyHardwareDatabaseOverrides: looking for "pci:10de:0774:1043:8290:0:capture"
kded(7549)/phonon (kded module) PS::AudioDevice::applyHardwareDatabaseOverrides: looking for "pci:10de:0774:1043:8290:1:capture"
kded(7549)/phonon (kded module) PS::AudioDevice::applyHardwareDatabaseOverrides: looking for "pci:10de:0774:1043:8290:0:playback"
kded(7549)/phonon (kded module) PS::AudioDevice::applyHardwareDatabaseOverrides: looking for "pci:10de:0774:1043:8290:1:playback"
kded(7549)/phonon (kded module) PhononServer::findVirtualDevices: ("iec958:CARD=NVidia,DEV=0" ("HDA NVidia, ALC662 Digital
IEC958 (S/PDIF) Digital Audio Output"))
kded(7549)/phonon (kded module) PS::AudioDevice::applyHardwareDatabaseOverrides: looking for "HDA NVidia, ALC662 Digital
IEC958 (S/PDIF) Digital Audio Output_playback"
kded(7549)/phonon (kded module) PS::AudioDevice::applyHardwareDatabaseOverrides: looking for "HDA NVidia, ALC662 Digital
IEC958 (S/PDIF) Digital Audio Output_capture"
kded(7549)/phonon (kded module) PhononServer::findDevices: Playback Devices: (
- "HDA NVidia (ALC662 Analog)", icon: "audio-card"
    uniqueId: "pci:10de:0774:1043:8290:0:playback", card: 0, device: 0
  index: -1, initialPreference: 36, available: true, advanced: false, DB name override: false
  description: "<html>This will try the following devices and use the first that works: <ol><li>ALSA: x-phonon:CARD=0,DEV=0</li><li>ALSA: plughw:CARD=0,DEV=0</li><li>OSS: /dev/sound/audio</li><li>OSS: /dev/sound/dsp</li></ol></html>"
  access: (deviceIds: ("x-phonon:CARD=0,DEV=0", "plughw:CARD=0,DEV=0") accessPreference:  11 driver  "ALSA"  playback, deviceIds: ("/dev/sound/audio") accessPreference:  0 driver  "OSS"  capture playback, deviceIds: ("/dev/sound/dsp") accessPreference:  0 driver  "OSS"  capture playback) ,  
- "HDA NVidia (ALC662 Digital)", icon: "audio-card"
    uniqueId: "pci:10de:0774:1043:8290:1:playback", card: 0, device: 1
  index: -2, initialPreference: 35, available: true, advanced: false, DB name override: false
  description: "<html>This will try the following devices and use the first that works: <ol><li>ALSA: x-phonon:CARD=0,DEV=1</li><li>ALSA: plughw:CARD=0,DEV=1</li><li>OSS: /dev/sound/adsp</li></ol></html>"
  access: (deviceIds: ("x-phonon:CARD=0,DEV=1", "plughw:CARD=0,DEV=1") accessPreference:  10 driver  "ALSA"  playback, deviceIds: ("/dev/sound/adsp") accessPreference:  0 driver  "OSS"  capture playback) ,  
- "HDA NVidia, ALC662 Digital (IEC958 (S/PDIF) Digital Audio Output)", icon: "audio-card"
    uniqueId: "HDA NVidia, ALC662 Digital
IEC958 (S/PDIF) Digital Audio Output_playback", card: -1, device: -1
  index: -3, initialPreference: 30, available: true, advanced: true, DB name override: false
  description: "<html>This will try the following devices and use the first that works: <ol><li>ALSA: iec958:CARD=NVidia,DEV=0</li></ol></html>"
  access: (deviceIds: ("iec958:CARD=NVidia,DEV=0") accessPreference:  0 driver  "ALSA"  capture playback) )
kded(7549)/phonon (kded module) PhononServer::findDevices: Capture Devices: (
- "HDA NVidia (ALC662 Analog)", icon: "audio-card"
    uniqueId: "pci:10de:0774:1043:8290:0:capture", card: 0, device: 0
  index: -4, initialPreference: 36, available: true, advanced: false, DB name override: false
  description: "<html>This will try the following devices and use the first that works: <ol><li>ALSA: x-phonon:CARD=0,DEV=0</li><li>ALSA: plughw:CARD=0,DEV=0</li><li>OSS: /dev/sound/dsp</li><li>OSS: /dev/sound/audio</li></ol></html>"
  access: (deviceIds: ("x-phonon:CARD=0,DEV=0", "plughw:CARD=0,DEV=0") accessPreference:  11 driver  "ALSA"  capture, deviceIds: ("/dev/sound/dsp") accessPreference:  0 driver  "OSS"  capture playback, deviceIds: ("/dev/sound/audio") accessPreference:  0 driver  "OSS"  capture playback) ,  
- "HDA NVidia (ALC662 Digital)", icon: "audio-card"
    uniqueId: "pci:10de:0774:1043:8290:1:capture", card: 0, device: 1
  index: -5, initialPreference: 35, available: true, advanced: true, DB name override: false
  description: "<html>This will try the following devices and use the first that works: <ol><li>ALSA: x-phonon:CARD=0,DEV=1</li><li>ALSA: plughw:CARD=0,DEV=1</li><li>OSS: /dev/sound/adsp</li></ol></html>"
  access: (deviceIds: ("x-phonon:CARD=0,DEV=1", "plughw:CARD=0,DEV=1") accessPreference:  10 driver  "ALSA"  capture, deviceIds: ("/dev/sound/adsp") accessPreference:  0 driver  "OSS"  capture playback) ,  
- "HDA NVidia, ALC662 Digital (IEC958 (S/PDIF) Digital Audio Output)", icon: "audio-card"
    uniqueId: "HDA NVidia, ALC662 Digital
IEC958 (S/PDIF) Digital Audio Output_capture", card: -1, device: -1
  index: -6, initialPreference: 30, available: true, advanced: true, DB name override: false
  description: "<html>This will try the following devices and use the first that works: <ol><li>ALSA: iec958:CARD=NVidia,DEV=0</li></ol></html>"
  access: (deviceIds: ("iec958:CARD=NVidia,DEV=0") accessPreference:  0 driver  "ALSA"  capture playback) )
kded(7549) KDEDModule::setModuleName: registerObject() successful for  "phononserver"
kded(7549)/kded4 Kded::loadModule: Successfully loaded module "phononserver"
amarok(7690)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-detVF0ko8/ksycoca4"
amarok(7690)/kdecore (KLibLoader) kde4Factory: The library "" does not offer a qt_plugin_instance function.
amarok(7690)/kdecore (KLibLoader) kde3Factory: The library "" does not offer an "init_phonon_xine" function.
amarok(7690) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
amarok(7690)/kdecore (KLibLoader) findLibraryInternal: plugins should not have a 'lib' prefix: "libamarok_collection-mtpcollection.so"
amarok(7690)/kdecore (KLibLoader) findLibraryInternal: plugins should not have a 'lib' prefix: "libamarok_collection-sqlcollection.so"
amarok(7690)/kdecore (KLibLoader) findLibraryInternal: plugins should not have a 'lib' prefix: "libamarok_collection-daapcollection.so"
QDBusObjectPath: invalid path ""
amarok(7690)/kdecore (KLibLoader) findLibraryInternal: plugins should not have a 'lib' prefix: "libamarok_collection-ipodcollection.so"
amarok(7690)/kdecore (KLibLoader) findLibraryInternal: plugins should not have a 'lib' prefix: "libamarok_massstorage-device.so"
kded(7549) KDEDModule::setModuleName: registerObject() successful for  "kdedglobalaccel"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::loadSettings: Loading group  "amarok"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::loadSettings: Loading group  "khotkeys"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::loadSettings: Loading group  "kwin"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcut::setKeys: "view_zoom_out" skipping because key "" is already taken
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::loadSettings: Loading group  "plasma"
kded(7549)/kded4 Kded::loadModule: Successfully loaded module "kdedglobalaccel"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta+A" for "amarok" : "playlist_add"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift++" for "amarok" : "seek_forward"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+-" for "amarok" : "seek_backward"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Z" for "amarok" : "prev"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta+B" for "amarok" : "next"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta++" for "amarok" : "increaseVolume"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta+-" for "amarok" : "decreaseVolume"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta+P" for "amarok" : "toggleMainWindow"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta+O" for "amarok" : "showOsd"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta+M" for "amarok" : "mute"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta+L" for "amarok" : "loveTrack"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta+1" for "amarok" : "rate1"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta+2" for "amarok" : "rate2"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta+3" for "amarok" : "rate3"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta+4" for "amarok" : "rate4"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta+5" for "amarok" : "rate5"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta+V" for "amarok" : "stop"
kded(7549)/kdecore (kdedglobalaccel) GlobalShortcutsRegistry::registerKey: Registering key "Meta+C" for "amarok" : "play_pause"
amarok(7690)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(7690)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(7690)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(7690)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(7690)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(7690)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
Object::connect: No such signal KLineEdit::downPressed()
amarok(7690)/libplasma Plasma::isPluginVersionCompatible: plugin is compiled against incompatible Plasma version   4294967295
amarok(7690)/libplasma Plasma::CoronaPrivate::addContainment: loading of containment "amarok_containment_vertical" failed.
amarok(7690) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"
amarok(7690)/libplasma Plasma::AppletPrivate::init: Check your constructor!  You probably want to be passing in a Service::Ptr  or a QVariantList with a valid storageid as arg[0].
amarok(7690)/libplasma Plasma::ViewPrivate::updateSceneRect: !!!!!!!!!!!!!!!!! setting the scene rect to QRectF(0,0 0x0) associated screen is -1
amarok(7690)/libplasma Plasma::ThemePrivate::config: using theme for app "amarok"
QObject::connect: Cannot connect (null)::updatedContainment( Containment* ) to Context::AppletToolbarAddItem::updatedContainment( Containment* )
amarok(7690)/libplasma Plasma::Containment::setScreen: setting screen to -1 and we are a 127
amarok(7690)/libplasma Plasma::Containment::setScreen: setting screen to  -1 and type is 127
amarok(7690)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(7690)/kio (bookmarks) KBookmarkManager::KBookmarkManager: starting KDirWatch for  "/home/det/.local/share//user-places.xbel"
amarok(7690)/kio (KDirListerCache) KDirListerCache::listDir: Listing directory: KUrl("trash:/")
amarok(7690)/kio (KDirListerCache) KDirListerCache::listDir: Listing directory: KUrl("file:///home/det")
amarok(7690)/libplasma Plasma::ViewPrivate::updateSceneRect: !!!!!!!!!!!!!!!!! setting the scene rect to QRectF(0,0 50x50) associated screen is -1
amarok(7690)/kio (KDirListerCache) KDirListerCache::listDir: Entry currently being listed: KUrl("trash:/") by (KDirLister(0x8c18d80) )
amarok(7690)/kio (Slave) KIO::Slave::createSlave: createSlave "trash" for KUrl("trash:/")
amarok(7690)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-det/amarokSa7690.slave-socket"
klauncher(7547)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-detVF0ko8/ksycoca4"
klauncher(7547)/kio (KLauncher) KLauncher::requestSlave: KLauncher: launching new slave  "kio_trash"  with protocol= "trash"  args= ("trash", "local:/tmp/ksocket-det/klauncherMT7547.slave-socket", "local:/tmp/ksocket-det/amarokSa7690.slave-socket")
kdeinit4: Got EXEC_NEW 'kio_trash' from launcher.
kdeinit4: preparing to launch 
klauncher(7547)/kio (KLauncher) KLauncher::processRequestReturn: "kio_trash" (pid 7702) up and running.
amarok(7690)/kio (Slave) KIO::Slave::createSlave: createSlave "file" for KUrl("file:///home/det")
amarok(7690)/kio (KIOConnection) KIO::ConnectionServer::listenForRemote: Listening on  "local:/tmp/ksocket-det/amaroksc7690.slave-socket"
klauncher(7547)/kio (KLauncher) KLauncher::requestSlave: KLauncher: launching new slave  "kio_file"  with protocol= "file"  args= ("file", "local:/tmp/ksocket-det/klauncherMT7547.slave-socket", "local:/tmp/ksocket-det/amaroksc7690.slave-socket")
kdeinit4: 
...Too much output, ignoring rest...
```

---

