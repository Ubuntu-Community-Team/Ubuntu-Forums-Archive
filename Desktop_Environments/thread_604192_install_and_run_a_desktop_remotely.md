---
title: "install and run a desktop remotely"
date: 2007-11-05
forum: Desktop Environments
---

### Post by lcslouis on 2007-11-05
i have a project i am working on
first i have a ubuntu 6.06 install on openvz
i need to install a desktop and make it accessible by remote
i can only execute commands by ssh i have no phyiscal access to the box
i am doing this a security project and need help.
i have full root the main box

---

### Post by Zelut on 2007-11-05
if you simply need to install a GUI on the machine remotely that is already installed with a base system you can just use:

> sudo apt-get install ubuntu-desktop

That will install the ubuntu (gnome) desktop on the base system.

---

### Post by lcslouis on 2007-11-05
yes but how to i set the desktop to allow remote logins via the cmd line all i have a ssh access to this pc.

---

### Post by deserthowler on 2007-11-05
If you want a remote login to a GUI, try VNC.  Here is a long thread for Kubuntu.
[http://ubuntuforums.org/showthread.php?t=259448](http://ubuntuforums.org/showthread.php?t=259448)

Earl

---

### Post by lcslouis on 2007-11-06
ok i have followed that now i am getting an error where dcopserver is not running how can i fix this?

---

### Post by gsiliceo on 2007-11-06
what exactly is this error thats is giving to you.

---

### Post by lcslouis on 2007-11-06
this is from my log file


```

Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Tue Nov  6 06:26:02 2007
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/share/X11/fonts/OTF, removing from list!
Could not init font path element /usr/share/X11/fonts/CID/, removing from list!
startkde: Starting up...
Xlib:  extension "XInputExtension" missing on display ":1.0".
Failed to get list of devices
Xlib:  extension "XInputExtension" missing on display ":1.0".
Failed to get list of devices
kbuildsycoca running...
Xlib:  extension "XInputExtension" missing on display ":1.0".
Failed to get list of devices
Server has no DPMS extension
Xlib:  extension "XFree86-Misc" missing on display ":1.0".
server does not have extension for "r rate" option
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/kde3/kcm_kdnssd.so: undefined symbol: init_kdnssd
Xlib:  extension "XInputExtension" missing on display ":1.0".
Failed to get list of devices
kaccess: ERROR: X server has not matching XKB extension
Xlib:  extension "XInputExtension" missing on display ":1.0".
Failed to get list of devices
Xlib:  extension "XInputExtension" missing on display ":1.0".
Failed to get list of devices
kded: Launching previous backup analyse.
kbuildsycoca running...
Reusing existing ksycoca
Xlib:  extension "XInputExtension" missing on display ":1.0".
Failed to get list of devices
kio (KSycoca): ERROR: No database available!
kdecore (KNetwork socket): WARNING: Error listening on socket: -1
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
Xlib:  extension "XInputExtension" missing on display ":1.0".
Failed to get list of devices
_IceTransSocketOpenCOTSClient: Unable to open socket for local
_IceTransOpen: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/9670
Session management error: Could not open network socket
socket() failed: : Cannot allocate memory
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
Xlib:  extension "XInputExtension" missing on display ":1.0".
Failed to get list of devices
_X11TransSocketOpenCOTSClient: Unable to open socket for local
_X11TransOpen: transport open failed for local/testserver.ucc-hq.org:1
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
socket() failed: : Cannot allocate memory
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: KUniqueApplication: Can't setup DCOP communication.
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
kdecore (KNetwork socket): WARNING: Error listening on socket: -1
kdecore (KNetwork socket): WARNING: Error listening on socket: -1
socket() failed: : Cannot allocate memory
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: KUniqueApplication: Can't setup DCOP communication.
socket() failed: : Cannot allocate memory
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: KUniqueApplication: Can't setup DCOP communication.
kicker: ERROR: Couldn't start kio_uiserver from kio_uiserver.desktop: KDEInit could not launch 'kio_uiserver'.
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
kdecore (KNetwork socket): WARNING: Error listening on socket: -1
kdecore (KNetwork socket): WARNING: Error listening on socket: -1
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
socket() failed: : Cannot allocate memory
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
There was an error setting up inter-process communications for KDE. The message returned by the system was:

Could not open network socket

Please check that the "dcopserver" program is running!
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPRef::call():  no DCOP client or client not attached error
socket() failed: : Cannot allocate memory
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
SocketOpen: socket() failed for local
SocketOpenCOTSClient: Unable to open socket for local
Open: transport open failed for local/testserver.ucc-hq.org:/tmp/.ICE-unix/dcop9650-1194330366
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: KUniqueApplication: Can't setup DCOP communication.
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /root/.DCOPserver_testserver.ucc-hq.org__1
and start dcopserver again.
---------------------------------

kdeinit: socketpair() failed!
: Cannot allocate memory
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: KUniqueApplication: Can't setup DCOP communication.
Xlib:  extension "XInputExtension" missing on display ":1.0".
Failed to get list of devices
Session management error: Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: KUniqueApplication: Parent process can't attach to DCOP.
Xlib:  extension "XInputExtension" missing on display "localhost:1.0".
Failed to get list of devices
Session management error: Could not open network socket
Xlib:  extension "XInputExtension" missing on display "localhost:1.0".
Failed to get list of devices
Session management error: Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /root/.DCOPserver_testserver.ucc-hq.org__1
and start dcopserver again.
---------------------------------

kdeinit: socketpair() failed!
: Cannot allocate memory
DCOPClient::attachInternal. Attach failed Could not open network socket

```

---

### Post by lcslouis on 2007-11-06
```
There was an error setting up inter-process communications for KDE. the message returned by the system was:

Could not open network socket

Please check that "dcopserver" program is running!
```

---

### Post by lcslouis on 2007-11-06
nevermind i looked at my vps beancounters and some limits were being knocked to the moon i adjusted and activated and the stuff works with no errors

but is there a way to configure mutiple users i would like to add a few users and disable the terminal window from loading

---

### Post by lcslouis on 2007-11-06
when i try to goto the users and groups it says users and groups not loaded. and way to load it?

---

### Post by lcslouis on 2007-11-06
ok i got all this working now i need to somehow configure the vnc for mutiple users as in i want to give 5 users access to the box each with a useraccount each vnc on a different port.

---

