---
title: "gdmflexiserver ERRORs 100, 3 when started via putty/cygwin-XWin"
date: 2006-06-21
forum: Desktop Environments
---

### Post by mikel64b on 2006-06-21
Hello!

I try to get an Ubuntu remote Desktop:

Server: Ubuntu 6.06
Client: WinXP, cygwin Xwin, putty

cygwn: X11 up and running (local xclock works)
Putty: X11 forwarding enabled, xclock, xterm are displayed on the XP box. Even nautilaus works.

gdmflexiserver -n startet _local_ on the ubuntu box shows a sign-on screen within a new window.

gdmflexiserver -n -d started on a putty console:

Empty, white X11 window opens on cygwin.

Putty console output:
Sending command: 'VERSION'
Got response: 'GDM 2.14.9'
Sending command: 'GET_CONFIG daemon/PidFile localhost:10.0'
Got response: 'OK /var/run/gdm.pid'
Sending command: 'CLOSE'
Sending command: 'VERSION'
Got response: 'GDM 2.14.9'
Sending command: 'AUTH_LOCAL 9b4d3ad153d80302d13a8bc5abf31bc8'
Got response: 'ERROR 100 Not authenticated'
Sending command: 'FLEXI_XNEST localhost:10 1000 9b4d3ad153d80302d13a8bc5abf31bc8 /home/mikel/.Xauthority'
Got response: 'ERROR 3 X failed'
Sending command: 'CLOSE'

X11 window closes.

Any idea?

THX in advance!

Mikel

---

