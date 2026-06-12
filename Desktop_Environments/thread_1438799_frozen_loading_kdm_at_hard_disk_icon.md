---
title: "frozen loading kdm at hard disk icon"
date: 2010-03-25
forum: Desktop Environments
---

### Post by linux000019 on 2010-03-25
what happens is, when i start up the laptop for the first time everyday, it loads normally up to the KDM loading screen, then completely freezes at the hard disk icon. if i press Ctrl+alt+f1 before the hard disk icon loads, i can get to console. 
 
also, sometimes afterwards, usually about 20-30 minutes of me rebooting into various recovery/kernel/memorychecks; ill retry a normal boot and tahdah it is working again. this makes me believe it could be a hardware problem.
 
open to suggestions or tips; anything at all. im pretty much still a linux newbie, only been using it for about 1 year. while mostly i use ubuntu, i just switched to kubuntu because i <3 amarok :D
 
however im thinking ill switch back to gnome. the default kernel with 9.10 ubuntu seemed to fit my laptop the best since it worked like a charm(although the upgraded 31.20 kernel broke my display so i had to revert to old kernel).

---

### Post by linux000019 on 2010-03-25
hey i did some forum searching and found someone recommending to post the .xsession log so here it is:
 
Xsession: X session started for ryan at Thu Mar 25 10:23:46 PDT 2010
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
X Error: XSyncBadAlarm 152
  Extension:    143 (Uknown extension)
  Minor opcode: 11 (Unknown request)
  Resource id:  0x0
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kglobalaccel.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kcminit_startup.so
X Error: XSyncBadAlarm 152
  Extension:    143 (Uknown extension)
  Minor opcode: 11 (Unknown request)
  Resource id:  0x0
kdeinit4: preparing to launch /usr/lib/libkdeinit4_ksmserver.so
<unknown program name>(1612)/ KStartupInfo::createNewStartupId: creating:  "LoD;1269537833;491440;1612_TIME0" : "unnamed app"
kephald starting up 
XRANDR error base:  162 
RRInput mask is set!! 
RandRScreen::loadSettings - adding mode:  63 1024 x 768 
RandRScreen::loadSettings - adding mode:  64 800 x 600 
RandRScreen::loadSettings - adding mode:  65 640 x 480 
RandRScreen::loadSettings - adding mode:  66 848 x 480 
RandRScreen::loadSettings - adding mode:  67 640 x 480 
RandRScreen::loadSettings - adding mode:  68 1024 x 768 
RandRScreen::loadSettings - adding mode:  69 800 x 600 
RandRScreen::loadSettings - adding crtc:  57 
RandRScreen::loadSettings - adding crtc:  58 
RandRScreen::loadSettings - adding output:  59 
Setting CRTC 0 on output "VGA1" (previous 0 ) 
RandRScreen::loadSettings - adding output:  60 
Setting CRTC 58 on output "LVDS1" (previous 0 ) 
CRTC outputs: (60) 
Output name: "LVDS1" 
Output refresh rate: 60.0038 
Output rect: QRect(0,0 1024x768) 
Output rotation: 1 
RandRScreen::loadSettings - adding output:  61 
Setting CRTC 0 on output "DVI1" (previous 0 ) 
RandRScreen::loadSettings - adding output:  62 
Setting CRTC 57 on output "TV1" (previous 0 ) 
CRTC outputs: (62) 
Output name: "TV1" 
Output refresh rate: 29.9692 
Output rect: QRect(0,0 1024x768) 
Output rotation: 1 
XRandROutputs::init 
  added output  59 
got a valid edid block... 
vendor code: "LPL" 
product id: 0 
serial number: 0 
  added output  60 
  added output  61 
  added output  62 
output: "DVI1" QRect(0,0 0x0) 0 false false 
output: "LVDS1" QRect(0,0 1024x768) 0 false false 
output: "TV1" QRect(0,0 1024x768) 0 false false 
output: "VGA1" QRect(0,0 0x0) 0 false false 
load xml 
connected: 2 
looking for current "LVDS1" 
known "*" has score: 0.125 
known "*" has score: 0.125 
looking for current "TV1" 
known "*" has score: 0.25 
screen: 0 QRect(0,0 1024x768) 
looking for a matching configuration... 
connected: 2 
looking for current "LVDS1" 
known "*" has score: 0.125 
known "*" has score: 0.125 
looking for current "TV1" 
known "*" has score: 0.25 
found outputs, known: false 
connected: 2 
looking for current "LVDS1" 
known "*" has score: 0.125 
known "*" has score: 0.125 
looking for current "TV1" 
known "*" has score: 0.25 
activate external configuration!! 
registered the service: true 
screens registered on the bus: true 
outputs registered on the bus: true 
configurations registered on the bus: true 
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXQueryDrawable" when GLX 1.3 is not supported!  This is an application bug!
kdeinit4: preparing to launch /usr/bin/kwrited
kdeinit4: preparing to launch /usr/lib/libkdeinit4_plasma-desktop.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kmixctrl.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_krunner.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_nepomukserver.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_nepomukserver.so
Nepomuk server already running.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kmix.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_konqueror.so
kdeinit4: preparing to launch /usr/bin/printer-applet
kdeinit4: preparing to launch /usr/bin/update-notifier-kde
kdeinit4: preparing to launch /usr/bin/update-notifier-kde
kdeinit4: preparing to launch /bin/sh
kdeinit4: preparing to launch /usr/bin/printer-applet
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kmix.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klipper.so
kdeinit4: preparing to launch /usr/bin/kblueplugd
kdeinit4: preparing to launch /usr/bin/knetworkmanager
Unable to connect to bluez.
<unknown program name>(1666)/: Communication problem with  "krunner" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." " 
<unknown program name>(1672)/: Communication problem with  "kmix" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." " 
<unknown program name>(1681)/: Communication problem with  "kmix" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." " 
<unknown program name>(1683)/: Communication problem with  "klipper" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." "

---

### Post by linux000019 on 2010-03-25
well, time to logoff and wait till tomorrow to start all over again.

---

