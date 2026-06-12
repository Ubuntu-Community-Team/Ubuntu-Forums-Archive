---
title: "KDE dies during startup"
date: 2009-11-01
forum: Desktop Environments
---

### Post by inportb on 2009-11-01
I just upgraded my Kubuntu Jaunty server to Karmic. After logging in via the KDM, the KDE splash screen starts loading and crashes back to the KDM screen.

So I bust out my working Kubuntu laptop and start a remote KDE session over Xephyr/SSH. It works.

Can anyone give me a hint on how to approach this problem? Here's the **.xsession-errors** dump:

```
Xsession: X session started for xyio at Sun Nov  1 10:41:59 EST 2009
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
startkde: Starting up...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
Invalid D-BUS member name 'idle-hint' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'is-local' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'x11-display-device' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'x11-display' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'display-device' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'remote-host-name' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'session-type' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'unix-user' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
X Error: XSyncBadAlarm 157
  Extension:    145 (Uknown extension)
  Minor opcode: 11 (Unknown request)
  Resource id:  0x0
X Error: XSyncBadAlarm 157
  Extension:    145 (Uknown extension)
  Minor opcode: 11 (Unknown request)
  Resource id:  0x0
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kglobalaccel.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kcminit_startup.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_ksmserver.so
<unknown program name>(3978)/ KStartupInfo::createNewStartupId: creating:  "phoenix;1257090121;413752;3978_TIME0" : "unnamed app"
kephald starting up 
XRANDR error base:  167 
RRInput mask is set!! 
RandRScreen::loadSettings - adding mode:  117 1280 x 1024 
RandRScreen::loadSettings - adding mode:  118 1280 x 960 
RandRScreen::loadSettings - adding mode:  119 1152 x 864 
RandRScreen::loadSettings - adding mode:  120 1152 x 864 
RandRScreen::loadSettings - adding mode:  121 1024 x 768 
RandRScreen::loadSettings - adding mode:  122 1024 x 768 
RandRScreen::loadSettings - adding mode:  123 800 x 600 
RandRScreen::loadSettings - adding mode:  124 800 x 600 
RandRScreen::loadSettings - adding mode:  125 640 x 480 
RandRScreen::loadSettings - adding crtc:  115 
RandRScreen::loadSettings - adding output:  116 
Setting CRTC 115 on output "default" (previous 0 ) 
CRTC outputs: (116) 
Output name: "default" 
Output refresh rate: 60 
Output rect: QRect(0,0 1280x1024) 
Output rotation: 1 
XRandROutputs::init 
  added output  116 
adding an output 0 with geom:  QRect(0,0 1280x1024) 
output: "SCREEN-0" QRect(0,0 1280x1024) 1635020626 true true 
load xml 
connected: 1 
looking for current "SCREEN-0" 
known "*" has score: 0.125 
screen: 0 QRect(0,0 1280x1024) 
looking for a matching configuration... 
connected: 1 
looking for current "SCREEN-0" 
known "*" has score: 0.125 
found outputs, known: false 
activate external configuration!! 
registered the service: true 
screens registered on the bus: true 
outputs registered on the bus: true 
configurations registered on the bus: true 
Qt-subapplication: Fatal IO error: client killed
kdeinit4: Fatal IO error: client killed
kdeinit4: sending SIGHUP to children.
klauncher: Exiting on signal 1
kdeinit4: Fatal IO error: client killed
kdeinit4: sending SIGHUP to children.
kglobalaccel: Fatal IO error: client killed
kded4: Fatal IO error: client killed
kwin: Fatal IO error: client killed
kdeinit4: sending SIGTERM to children.
kdeinit4: Exit.
kdeinit4: sending SIGTERM to children.
kdeinit4: Exit.
```

Thanks for the help, guys.

---

### Post by inportb on 2009-11-02
(I have filed a report on Launchpad: [with kernel 2.6.31-14-generic my X server crashes during KDE 4.3.2 startup]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/471646"))

So like, startx directly at the console yields

```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux phoenix 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: root=UUID=c29b60cc-e6ef-450c-b3c5-ea761c6e3416 ro  single
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@)
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov  2 14:39:52 2009
(==) Using config file: "/etc/X11/xorg.conf"
Fulfilled via DRI at 20976640
Freed 20976640 (pool 2)
X: main/renderbuffer.c:2159: _mesa_reference_renderbuffer: Assertion `oldRb->Magic == 0xaabbccdd' failed.
xinit:  connection to X server lost.
```

The relevant line seems to be

```
X: main/renderbuffer.c:2159: _mesa_reference_renderbuffer: Assertion `oldRb->Magic == 0xaabbccdd' failed.
```

Furthermore, I just tried booting into the older kernel 2.6.28-16, and it works. So... perhaps a driver has broken? I'm using the OpenChrome driver, and here's my Xorg.conf --

```
Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"      "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Option          "DPMS"
        HorizSync       31.5-65.2       # 31.5-37.9
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Depth    24
                Modes    "1280x1024"
        EndSubSection
EndSection
```

---

### Post by inportb on 2009-11-02
I noticed that making the Xorg device option "NoAccel" "true" allows KDE to start, but screen updates are exceptionally slow.

---

### Post by CHaoSlayeR on 2010-02-12
I have the same problem for some days now on one of my machines.

I'm using a ATI/AMD card (Radeon HD2400PRO) and since kernel 2.6.31-19 I have this problem.

The following things worked for me to log in successfully:
[LIST=1]
[*]Disable KDE4 compositing (~/.kde/share/config/kwinrc):```
[Compositing]
...
Enabled=false
```
[*]Disable AIGLX completely but preserve 2D acceleration (/etc/X11/xorg.conf):```
Section "ServerFlags"
...
    Option "AIGLX" "off"
EndSection
```
[*]Use XFCE instead (although OpenGL things fails there too, but at least all WM tweaks can be enabled safely)
[/LIST]

My configuration worked fine with at least kernel 2.6.31-18 and so I'm unsure if this is really a kernel issue. I think it is more of a driver issue here.

Your driver version seems to be compiled for 2.6.24 and we all know that between 2.6.28 and 2.6.31 (especially from 2.6.30 to 2.6.31) a lot of gfx stuff has changed in the kernel. So what you can try is to use the driver from "xorg-edgers":

[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=karmic)

They have a recent version.

Good luck.

However I will try the 2.6.32 and/or 2.6.33 mainline kernel to test whether my problem is kernel related.

C]-[aoZ

---

