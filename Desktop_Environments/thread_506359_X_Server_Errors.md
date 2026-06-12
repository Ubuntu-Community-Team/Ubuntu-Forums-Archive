---
title: "X Server Errors"
date: 2007-07-21
forum: Desktop Environments
---

### Post by kseise on 2007-07-21
My X Server crashes everytime I attempt to log into gnome.  I am able to enter KDE just fine.  It is only in gnome that I have the problem.

I have a .xsession-errors file that looks like this:
> 
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "kseise"
/etc/gdm/Xsession: Beginning session setup...
startkde: Starting up...
startkde: kpersonalizer not found! Please install to properly configure your user.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
*** attempt to put segment in horiz list twice
kdesktop: WARNING: Pixmap not found for mimetype application/vnd.google-earth.kml+xml
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x44
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
kdecore (KProcess): WARNING: _attachPty() 15
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400270
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/firefox/plugins/libunixprintplugin.so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/firefox/plugins/libunixprintplugin.so: undefined symbol: NP_GetMIMEDescription
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
kbluetoothd: WARNING: No usable bluetooth device found.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x813c950 ): KAccel object already contains an action name "file_quit"
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x813c950 ): KAccel object already contains an action name "file_quit"
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x44
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x44
QFile::open: No file name specified
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400753
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x140053d
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x140053d
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400791
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x1400791
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400792
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x1400792
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x44
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x2c092fc
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14007fa
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400793
QClipboard::setData: Cannot set X11 selection owner for PRIMARY
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x44
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x44
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14009bd
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14009cd
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x14009cd
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14009ed
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x14009ed
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14009ee
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x14009ee
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14009ef
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x14009ef
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400a35
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x1400a35
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400a6c
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x1400a6c
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400abc
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x1400abc
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400ae6
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x1400ae6
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400b03
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x1400b03
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400b29
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x1400b29
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400b4b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x1400b4b
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x44
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x44
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x140124f
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x140124f
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400b68
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x1400b68
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1401688
Google Earth has caught signal 11.

Stacktrace from glibc:
  ./googleearth-bin(__gxx_personality_v0+0x1f0) [0x8057b84]
  ./googleearth-bin [0x8057f6b]
  [0xffffe420]


kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KLauncher): ERROR: SlavePool: No communication with slave.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x44



I have no idea what I am doing with this.  Please help me restore gnome.

---

