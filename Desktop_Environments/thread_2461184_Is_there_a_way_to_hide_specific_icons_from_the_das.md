---
title: "Is there a way to hide specific icons from the dash?"
date: 2021-04-26
forum: Desktop Environments
---

### Post by dokimira on 2021-04-26
Hello all! 

A little bit of system info:

i5-6300U, 8 gigs of 2133 Mhz SODIMM (single stick),  Intel HD 520, 256 GB SK Hynix SC308 NVME SSD, and a 1366 x 768 display. Ultrabook, running Ubuntu 20.04 LTS.

As for my question, is there a way to hide specific icons from the dash, but still be able to launch them by either directly navigating to the files of the program like you can with some Windows programs, or through terminal?

---

### Post by scorp123 on 2021-04-26
> **dokimira said:**
>  is there a way to hide specific icons from the dash, but still be able to launch them by either directly navigating to the files of the program like you can with some Windows programs, or through terminal?

Yes, you could manipulate their *.desktop file that launches them. There are 2 x parameters you could work with:
[LIST]
[*]OnlyShowIn=
[*]NotShowIn=
[/LIST]

For example... On my system there's a file **/usr/share/applications/org.gnome.FileRoller.desktop** for the "FileRoller" archive manager app. On my system it looks like this:
```

[Desktop Entry]
Name=Archive Manager
Comment=Create and modify an archive
# Translators: Search terms to find this application. Do NOT translate or localize the semicolons! The list MUST also end with a semicolon!
Keywords=zip;tar;extract;unpack;
TryExec=file-roller
Exec=file-roller %U
StartupNotify=true
Terminal=false
Type=Application
# Translators: Do NOT translate or transliterate this text (this is an icon file name)!
Icon=org.gnome.ArchiveManager
Categories=GTK;GNOME;Utility;Archiving;Compression;X-GNOME-Utilities;
**[COLOR="#FF0000"]NotShowIn=KDE;[/COLOR]**
MimeType=application/bzip2;application/gzip;application/vnd.android.package-archive;application/vnd.ms-cab-compressed;application/vnd.debian.binary-package;application/x-7z-compressed;application/x-7z-compressed-tar;application/x-ace;application/x-alz;application/x-ar;application/x-archive;application/x-arj;application/x-brotli;application/x-bzip-brotli-tar;application/x-bzip;application/x-bzip-compressed-tar;application/x-bzip1;application/x-bzip1-compressed-tar;application/x-cabinet;application/x-cd-image;application/x-compress;application/x-compressed-tar;application/x-cpio;application/x-chrome-extension;application/x-deb;application/x-ear;application/x-ms-dos-executable;application/x-gtar;application/x-gzip;application/x-gzpostscript;application/x-java-archive;application/x-lha;application/x-lhz;application/x-lrzip;application/x-lrzip-compressed-tar;application/x-lz4;application/x-lzip;application/x-lzip-compressed-tar;application/x-lzma;application/x-lzma-compressed-tar;application/x-lzop;application/x-lz4-compressed-tar;application/x-ms-wim;application/x-rar;application/x-rar-compressed;application/x-rpm;application/x-source-rpm;application/x-rzip;application/x-rzip-compressed-tar;application/x-tar;application/x-tarz;application/x-tzo;application/x-stuffit;application/x-war;application/x-xar;application/x-xz;application/x-xz-compressed-tar;application/x-zip;application/x-zip-compressed;application/x-zstd-compressed-tar;application/x-zoo;application/zip;application/zstd;
X-GNOME-DocPath=file-roller/file-roller.xml
X-GNOME-UsesNotifications=true
X-Ubuntu-Gettext-Domain=file-roller

```

Thanks to that **"NotShowIn=KDE;"** entry above I should never ever get to see an icon for it in KDE, but it should still be visible in e.g. GNOME, XFCE, Unity, etc.. And I could still launch it via terminal if I so desired ...

Another example:

The file **/usr/share/applications/org.gnome.PowerStats.desktop** ... it looks like this:

```

[Desktop Entry]
Name=Power Statistics
Comment=Observe power management
# Translators: Search terms to find this application. Do NOT translate or localize the semicolons! The list MUST also end with a semicolon!
Keywords=battery;consumption;charge;
# Translators: Do NOT translate or transliterate this text (this is an icon file name)!
Icon=org.gnome.PowerStats
Exec=gnome-power-statistics
Terminal=false
Type=Application
Categories=GNOME;GTK;System;Monitor;
**[COLOR="#FF0000"]OnlyShowIn=GNOME;Unity;[/COLOR]**
StartupNotify=true
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-power-manager
X-GNOME-Bugzilla-Component=gnome-power-statistics
X-GNOME-Bugzilla-Version=3.32.0
X-Desktop-File-Install-Version=0.10
X-Ubuntu-Gettext-Domain=gnome-power-manager

```

Thanks to that **"OnlyShowIn=GNOME;Unity;"** I should only ever get to see that icon in GNOME and Unity .. but never in KDE or XFCE or any other desktop.

You need to be root (e.g. use "sudo") to edit the files in **/usr/share/applications/** but you can definitely manipulate menu entries that way and make them hide in certain desktop environments. Or you could move the files you don't want away (do not delete them though!!) to a different location, or rename them into something the system won't recognise as launcher (e.g. you rename the file **vlc.desktop** into **vlc.desktop_DISABLED**) which very likely would cause the application to "disappear" from the menus.


Give that a try? And let us know if it worked.

---

### Post by Holger_Gehrke on 2021-04-26
> **scorp123 said:**
> 
You need to be root (e.g. use "sudo") to edit the files in **/usr/share/applications/** but you can definitely manipulate menu entries that way and make them hide in certain desktop environments. Or you could move the files you don't want away (do not delete them though!!) to a different location, or rename them into something the system won't recognise as launcher (e.g. you rename the file **vlc.desktop** into **vlc.desktop_DISABLED**) which very likely would cause the application to "disappear" from the menus.

Give that a try? And let us know if it worked.

Another way: you can 'remove' icons by copying them to the user-specific directory for desktop files ('~/.local/share/applications/') and putting either 'NoDisplay=true' (which will leave associations with MIME-types working) or 'Hidden=true' (which will make it as if the .desktop file didn't exist at all) into the copy. The user-specific location is read after the system-wide one and overrules it. No need to be root for this, since the files are world-readable and the copy goes into a directory you (should) own.

Holger

---

### Post by dokimira on 2021-04-26
> **scorp123 said:**
> 

You need to be root (e.g. use "sudo") to edit the files in **/usr/share/applications/** but you can definitely manipulate menu entries that way and make them hide in certain desktop environments. Or you could move the files you don't want away (do not delete them though!!) to a different location, or rename them into something the system won't recognise as launcher (e.g. you rename the file **vlc.desktop** into **vlc.desktop_DISABLED**) which very likely would cause the application to "disappear" from the menus.


Give that a try? And let us know if it worked.

..I know how to use sudo in terminal, but overall i'm pretty new to Linux. Is this done in terminal, or if it is done in the GUI, how do you get the root permissions?

---

### Post by Dennis N on 2021-04-26
Application Icons appear in Ubuntu dock: 
1) only when the application is running, unless: 
2) they are pinned to the dock - which means kept there at all times (as "favorites"). 

Their state is toggled from right-clicking on the dock icon. Choose either "Add to favorites" or "Remove from favorites".

If you rename the desktop file as suggested, realize that the application won't show in your application grid or as a search result either.

---

