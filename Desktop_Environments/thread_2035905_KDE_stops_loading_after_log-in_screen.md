---
title: "KDE stops loading after log-in screen"
date: 2012-07-31
forum: Desktop Environments
---

### Post by arnasd on 2012-07-31
hi guys,

i've encountered pretty stubborn problem and couldn't find anything useful with search.
my problem is that after kernel upgrade to 3.2.0-27-generic, KDE 12.04 stops loading after the log-in screen. after entering username/password, login window disappears and i'm left with mouse cursor and default screen background. alt+tab works, but it shows that there are "no active windows" whatsoever.
i tried to check the X0 log in /var/ directory, but it seems to contain any major error messages. dmesg also does not have any major messages.
disk usage is mild, more that 16gb available, so this is not a space issue.

i could load the root user and tried to start kde with "startx" command from shell, but i received the following error:
Could not create lock file in /tmp/tx0-lock
Please consult the The X.org Foundation support

ddxSigGiveup:closing log
xinit: giving up
xinit: unable to connect to xserver: Connection refused
xinit: server error
xauth: error in loading authority file /root/.Xauthority

it was launched under root user but it should not have any access problems.

do you have any ideas what could i check?

---

### Post by arnasd on 2012-08-01
my .xsession-errors log file:

> 
Xsession: X session started for ard at Wed Aug  1 10:41:29 EEST 2012
localuser:ard being added to access control list
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
OpenGL vendor string:                   NVIDIA Corporation
OpenGL renderer string:                 GeForce GTX 460/PCIe/SSE2
OpenGL version string:                  4.2.0 NVIDIA 295.40
OpenGL shading language version string: 4.20 NVIDIA via Cg compiler
Driver:                                 NVIDIA
Driver version:                         295.40
GPU class:                              GF100
OpenGL version:                         4.2
GLSL version:                           4.20
X server version:                       1.11.3
Linux kernel version:                   3.2
Direct rendering:                       yes
Requires strict binding:                no
GLSL shaders:                           yes
Texture NPOT support:                   yes
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
kbuildsycoca4 running...
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: name 'org.kde.kglobalaccel' had owner '' but we thought it was ':1.7'
kwin(2103): Invalid framebuffer status:  "GL_FRAMEBUFFER_UNSUPPORTED" 
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
ImageProvider supports Pixmap type but has not implemented requestPixmap()
file:///usr/share/kde4/apps/kwin/tabbox/thumbnails.qml:139:9: QML Image: Failed to get image from provider: image://client/-1/-517812004-0
file:///usr/share/kde4/apps/kwin/tabbox/thumbnails.qml:101: Unable to assign QString to qulonglong
ImageProvider supports Pixmap type but has not implemented requestPixmap()
file:///usr/share/kde4/apps/kwin/tabbox/thumbnails.qml:139:9: QML Image: Failed to get image from provider: image://client/0/-517812004-0
ImageProvider supports Pixmap type but has not implemented requestPixmap()
file:///usr/share/kde4/apps/kwin/tabbox/thumbnails.qml:139:9: QML Image: Failed to get image from provider: image://client/0/-517812004-1
ImageProvider supports Pixmap type but has not implemented requestPixmap()
file:///usr/share/kde4/apps/kwin/tabbox/thumbnails.qml:139:9: QML Image: Failed to get image from provider: image://client/0/-517812004-2
file:///usr/share/kde4/apps/kwin/tabbox/thumbnails.qml:101: Unable to assign QString to qulonglong


---

### Post by arnasd on 2012-08-01
my dmesg file:
[http://pastebin.com/dSrL4D3M](http://pastebin.com/dSrL4D3M)

i tried to to load with and without ~/.kde/share/config folder, but nothing changed.

---

### Post by arnasd on 2012-08-01
i tried removing ~/.kde /var/tmp/kdecache-ard .dmrc, also tried to stop kdm and start kdm, but i still could not log in. every attempt results in blank screen with mouse cursor only.

---

### Post by tartalo on 2012-08-01
> **arnasd said:**
> (...)
xauth: error in loading authority file /root/.Xauthority

it was launched under root user (...)

Related? [https://bbs.archlinux.org/viewtopic.php?id=73552](https://bbs.archlinux.org/viewtopic.php?id=73552)

---

### Post by arnasd on 2012-08-09
well i think that the problem with .XAuthority came when i tried to start kdm when kdm was already running.
it seems that kde crashes at some point but i can't find any particular error in logs. does it write any other logs, other than  .xsession-errors ?

---

### Post by SeijiSensei on 2012-08-09
Perhaps the root partition is mounted read-only?  Can you create any files at all?

---

### Post by arnasd on 2012-08-12
my root partition is mounted correctly and i have needed permisions.

i have stopped kdm, deleted .xsession-errors log file, started kdm and tried to login. so this .xsession log is "fresh":
> 
Xsession: X session started for ard at Sun Aug 12 23:42:33 EEST 2012
localuser:ard being added to access control list
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
OpenGL vendor string:                   NVIDIA Corporation
OpenGL renderer string:                 GeForce GTX 460/PCIe/SSE2
OpenGL version string:                  4.2.0 NVIDIA 295.40
OpenGL shading language version string: 4.20 NVIDIA via Cg compiler
Driver:                                 NVIDIA
Driver version:                         295.40
GPU class:                              GF100
OpenGL version:                         4.2
GLSL version:                           4.20
X server version:                       1.11.3
Linux kernel version:                   3.2
Direct rendering:                       yes
Requires strict binding:                no
GLSL shaders:                           yes
Texture NPOT support:                   yes
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
kbuildsycoca4 running...
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: name 'org.kde.kglobalaccel' had owner '' but we thought it was ':1.7'
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
kded4: Fatal IO error: client killed
kdeinit4: Fatal IO error: client killed
klauncher: Exiting on signal 15
kdeinit4: Fatal IO error: client killed
x-window-manager: Fatal IO error: client killed
knotify4: Fatal IO error: client killed
kglobalaccel: Fatal IO error: client killed
kactivitymanagerd: Fatal IO error: client killed


---

### Post by volkyl on 2012-08-28
arnasd, did you ever find a solution to this problem.  I just hit it myself.

---

### Post by arnasd on 2012-08-29
no, actually i did not. i've posted on kde forums but could not find anything. here is the link, maybe you will find it usefull:
[http://forum.kde.org/viewtopic.php?f=15&t=107335](http://forum.kde.org/viewtopic.php?f=15&t=107335)

mainly they are suggesting trying to log on with freshly created user, but that did not help me. i tried to delete my all local config files /home/username/.* but it did not help either.

volkyl, can you post your error logs? maybe there will be some similarities or differences. it could help find the solution to this.

i could do a fresh kubuntu install, but i have pretty complex double hard drive system with raid0 and raid1 implemented on root and storage partitions and i want to avoid any kind of configuration/alteration of existing volume configurations.

---

