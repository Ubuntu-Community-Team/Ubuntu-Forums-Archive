---
title: "[SOLVED] Concurrent Session Fails"
date: 2008-10-15
forum: Desktop Environments
---

### Post by gxbacher on 2008-10-15
Kubuntu Hardy 8.04

I have a problem with multiple sessions for differing users.

I have 2 users, A and B. Either one can log in fine when they are the only running session. User A can log in multiple times with no problems ("Start new session"...).

BUT, if user A is logged in and user B attempts to start a new session, something goes horribly wrong - the desktop starts to load, but the desktop icons never show up and nothing will run. Menus seem to work, but clicking an item doesn't work. Some programs fail to do anything, others start to draw the window but the contents never appear and it just hangs. Can't log out. About the only thing that works is "Switch session" and killing X (Ctrl-Alt-Backspace).

I noticed an .xsession-errors file in user B's home folder, and I'll attach it. I've Googled the obvious errors/warnings but haven't come up with anything yet. I'm not a newbie but I'm a bit out of my league with this X stuff. 

Thanks in advance.

```
Xsession: X session started for UserB at Tue Oct 14 20:28:10 EDT 2008
Setting IM through im-switch for locale=en_US.
Start IM through /home/UserB/.xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/scim-bridge.
iceauth:  creating new authority file /home/UserB/.ICEauthority
startkde: Starting up...
/usr/bin/iceauth:  creating new authority file /home/UserB/.ICEauthority
kbuildsycoca running...
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
Ignored duplicate item: Printing
Ignored duplicate item: Gnumeric Spreadsheet
Ignored duplicate item: Samba
Ignored duplicate item: Software Sources
Ignored duplicate item: Printing
Ignored duplicate item: Partition Editor
Ignored duplicate item: NVIDIA X Server Settings
Ignored duplicate item: Shared Folders
Ignored duplicate item: Update Manager
Ignored duplicate item: Network
Ignored duplicate item: Time and Date
Ignored duplicate item: System Monitor
Ignored duplicate item: Login Window
Ignored duplicate item: Services
Ignored duplicate item: Users and Groups
Ignored duplicate item: Hardware Testing
Ignored duplicate item: Network Tools
Ignored duplicate item: KArm
Ignored duplicate item: KNotes
Ignored duplicate item: Kontact
Ignored duplicate item: Strigi
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
GCJ PLUGIN: thread 0x65f680: NP_GetValue
GCJ PLUGIN: thread 0x65f680: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x65f680: NP_GetValue return
GCJ PLUGIN: thread 0x65f680: NP_GetValue
GCJ PLUGIN: thread 0x65f680: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x65f680: NP_GetValue return
GCJ PLUGIN: thread 0x65f680: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x65f680: NP_GetMIMEDescription return
kdecore (KProcess): WARNING: _attachPty() 19
Connection failure: Connection refused
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
GCJ PLUGIN: thread 0x65dce0: NP_GetValue
GCJ PLUGIN: thread 0x65dce0: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x65dce0: NP_GetValue return
GCJ PLUGIN: thread 0x65dce0: NP_GetValue
GCJ PLUGIN: thread 0x65dce0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x65dce0: NP_GetValue return
GCJ PLUGIN: thread 0x65dce0: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x65dce0: NP_GetMIMEDescription return
** Message: another SSH agent is running at: /tmp/ssh-BCmOv15833/agent.15833
Unable to connect to bluez.
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
GCJ PLUGIN: thread 0x65dce0: NP_GetValue
GCJ PLUGIN: thread 0x65dce0: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x65dce0: NP_GetValue return
GCJ PLUGIN: thread 0x65dce0: NP_GetValue
GCJ PLUGIN: thread 0x65dce0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x65dce0: NP_GetValue return
GCJ PLUGIN: thread 0x65dce0: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x65dce0: NP_GetMIMEDescription return
kbuildsycoca running...
Reusing existing ksycoca
DCOP Cleaning up dead connections.
ERROR: Only administrators can use this function.
kdeinit: Fatal IO error: client killed
kdeinit: sending SIGHUP to children.
skim: sighandler called
kdeinit: sending SIGTERM to children.
kdeinit: Exit.
*** kdesktop got signal 1 (Exiting)
*** kdesktop got signal 15 (Exiting)
klauncher: Exiting on signal 15
klauncher: Fatal IO error: client killed
skim: sighandler called
kwin: Fatal IO error: client killed
kicker: sighandler called
kicker: sighandler called
kicker: Fatal IO error: client killed
kdeinit: Fatal IO error: client killed
kdeinit: sending SIGHUP to children.
skim: sighandler called
kicker: sighandler called
kdeinit: sending SIGTERM to children.
kdeinit: Exit.
skim: sighandler called

```

---

### Post by gxbacher on 2008-10-15
Forget it. I just deleted every config file and folder that wasn't user data. This user hadn't really modified the environment yet so they didn't care. When they logged in next time, it worked fine.

---

