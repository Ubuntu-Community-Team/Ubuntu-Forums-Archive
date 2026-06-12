---
title: "problem of open 9.04 desktop"
date: 2009-06-24
forum: Desktop Environments
---

### Post by freesky3555 on 2009-06-24
display card is ATI RADEON 9550 that 9.04 not support. so usred open sources drive. then becuse change display Resolution the screen changed mess. this is $HOME/.xsession-errors, please tell me why 
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=zh_CN.
Start IM through /etc/X11/xinit/xinput.d/zh_CN linked to /etc/X11/xinit/xinput.d/scim-bridge.
Smart Common Input Method 1.4.7

Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
GTK Panel of SCIM 1.4.7

Starting SCIM as daemon ...
SCIM has been successfully launched.
GNOME_KEYRING_SOCKET=/tmp/keyring-zMyYjC/socket
SSH_AUTH_SOCK=/tmp/keyring-zMyYjC/socket.ssh
&#31383;&#21475;&#31649;&#29702;&#22120;&#35686;&#21578;&#65306; &#26080;&#27861;&#35835;&#21462;&#20445;&#23384;&#30340;&#20250;&#35805;&#25991;&#20214; /home/fred/.config/metacity/sessions/109314989ea87e0efb124568477698372600000038680024.ms&#65306;&#25171;&#24320;&#25991;&#20214;“/home/fred/.config/metacity/sessions/109314989ea87e0efb124568477698372600000038680024.ms”&#22833;&#36133;&#65306;&#27809;&#26377;&#35813;&#25991;&#20214;&#25110;&#30446;&#24405;
** (gnome-panel:4196): DEBUG: Adding applet 0.
** (gnome-panel:4196): DEBUG: Initialized Panel Applet Signaler.
x-session-manager[3868]: WARNING: Could not launch application 'trackerd.desktop': Unable to start application: &#25191;&#34892;&#23376;&#36827;&#31243;“trackerd”&#22833;&#36133;(&#27809;&#26377;&#35813;&#25991;&#20214;&#25110;&#30446;&#24405;)
** (gnome-panel:4196): DEBUG: Adding applet 1.
Failure: Module initalization failed
** (gnome-panel:4196): DEBUG: Adding applet 2.
x-session-manager[3868]: WARNING: Could not launch application 'tracker-applet.desktop': Unable to start application: &#25191;&#34892;&#23376;&#36827;&#31243;“tracker-applet”&#22833;&#36133;(&#27809;&#26377;&#35813;&#25991;&#20214;&#25110;&#30446;&#24405;)
** (gnome-panel:4196): DEBUG: Adding applet 3.
** (gnome-panel:4196): DEBUG: Adding applet 4.
** (gnome-panel:4196): DEBUG: Adding applet 5.
** (gnome-panel:4196): DEBUG: Adding applet 6.
** (gnome-panel:4196): DEBUG: Adding applet 7.
** (gnome-panel:4196): DEBUG: Adding applet 8.

** (nautilus:4215): WARNING **: Unable to add monitor: &#19981;&#25903;&#25345;
** (gnome-panel:4196): DEBUG: Adding applet 9.
** (gnome-panel:4196): DEBUG: Adding applet 10.
** (gnome-panel:4196): DEBUG: Adding applet 11.
** (gnome-panel:4196): DEBUG: Adding applet 12.
** (gnome-panel:4196): DEBUG: Adding applet 13.

(gnome-panel:4196): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:4196): DEBUG: Adding applet 14.
evolution-alarm-notify-Message: Setting timeout for 1585 1245686400 1245684815
evolution-alarm-notify-Message:  Tue Jun 23 00:00:00 2009

evolution-alarm-notify-Message:  Mon Jun 22 23:33:35 2009

** (update-notifier:4245): DEBUG: /usr/lib/update-notifier/apt-check returned 239 (security: 55)
** (update-notifier:4245): DEBUG: crashreport_check


** (tsclient:9353): WARNING **: 
vncviewer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory



(tsclient:9353): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.20.1/gobject/gsignal.c:2387: instance `0x8fa38e0' has no handler with id `1098'
Loading simple Config module ...
Creating backend ...
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSLoading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.7

gpgv: &#20110; 2009&#24180;04&#26376;20&#26085; &#26143;&#26399;&#19968; 22&#26102;02&#20998;22&#31186; CST &#21019;&#24314;&#30340;&#31614;&#21517;&#65292;&#20351;&#29992; DSA&#65292;&#38053;&#21273;&#21495; FBB75451
gpgv: &#23436;&#22909;&#30340;&#31614;&#21517;&#65292;&#26469;&#33258;&#20110;“Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>”
** (update-notifier:4245): DEBUG: /usr/lib/update-notifier/apt-check returned 239 (security: 55)
evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1245686400
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1245772800 1245686400
evolution-alarm-notify-Message:  Wed Jun 24 00:00:00 2009

evolution-alarm-notify-Message:  Tue Jun 23 00:00:00 2009

23/06/2009 00&#26102;20&#20998;59&#31186; Autoprobing TCP port in (all) network interface
23/06/2009 00&#26102;20&#20998;59&#31186; Listening IPv{4,6}://*:5900
23/06/2009 00&#26102;20&#20998;59&#31186; Autoprobing selected port 5900
23/06/2009 00&#26102;20&#20998;59&#31186; Advertising security type: 'TLS' (18)
23/06/2009 00&#26102;20&#20998;59&#31186; Advertising authentication type: 'No Authentication' (1)
23/06/2009 00&#26102;20&#20998;59&#31186; Advertising security type: 'No Authentication' (1)
23/06/2009 00&#26102;21&#20998;07&#31186; [IPv6] Got connection from client ::ffff:189.38.80.51
23/06/2009 00&#26102;21&#20998;07&#31186;   other clients:
23/06/2009 00&#26102;21&#20998;08&#31186; rfbProcessClientProtocolVersion: client gone
23/06/2009 00&#26102;21&#20998;08&#31186; Client ::ffff:189.38.80.51 gone
23/06/2009 00&#26102;21&#20998;08&#31186; Statistics:
23/06/2009 00&#26102;21&#20998;08&#31186;   framebuffer updates 0, rectangles 0, bytes 0
23/06/2009 00&#26102;22&#20998;03&#31186; [IPv6] Got connection from client ::ffff:192.168.0.102
23/06/2009 00&#26102;22&#20998;03&#31186;   other clients:
23/06/2009 00&#26102;22&#20998;04&#31186; Client Protocol Version 3.7
23/06/2009 00&#26102;22&#20998;04&#31186; Advertising security type 18
23/06/2009 00&#26102;22&#20998;04&#31186; Advertising security type 1
23/06/2009 00&#26102;22&#20998;06&#31186; Client returned security type 18
23/06/2009 00&#26102;22&#20998;11&#31186; Advertising authentication type 1
23/06/2009 00&#26102;22&#20998;11&#31186; Client returned authentication type 1
23/06/2009 00&#26102;22&#20998;21&#31186; rfbProcessClientNormalMessage: ignoring unknown encoding type -258
23/06/2009 00&#26102;22&#20998;21&#31186; Enabling NewFBSize protocol extension for client ::ffff:192.168.0.102
23/06/2009 00&#26102;22&#20998;21&#31186; rfbProcessClientNormalMessage: ignoring unknown encoding type 1464686185
23/06/2009 00&#26102;22&#20998;21&#31186; rfbProcessClientNormalMessage: ignoring unknown encoding type -257
23/06/2009 00&#26102;22&#20998;50&#31186; rfbProcessClientNormalMessage: read: &#36164;&#28304;&#20020;&#26102;&#19981;&#21487;&#29992;
23/06/2009 00&#26102;22&#20998;50&#31186; Client ::ffff:192.168.0.102 gone
23/06/2009 00&#26102;22&#20998;50&#31186; Statistics:
23/06/2009 00&#26102;22&#20998;50&#31186;   key events received 6, pointer events 1245
23/06/2009 00&#26102;22&#20998;50&#31186;   framebuffer updates 69, rectangles 302, bytes 649942
23/06/2009 00&#26102;22&#20998;50&#31186;     tight rectangles 302, bytes 649942
23/06/2009 00&#26102;22&#20998;50&#31186;   raw bytes equivalent 20750928, compression ratio 31.927354

** (tsclient:22226): WARNING **: 
ERROR: channel_register
WARNING: Initializing sound-support failed!
ERROR: 192.168.0.102: unable to connect



** (tsclient:22226): WARNING **: 
ERROR: channel_register
WARNING: Initializing sound-support failed!
ERROR: 192.168.0.102: unable to connect



(tsclient:22226): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.20.1/gobject/gsignal.c:2387: instance `0x92848e0' has no handler with id `1098'

** (tsclient:22226): WARNING **: 
vncviewer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory



(tsclient:22226): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.20.1/gobject/gsignal.c:2387: instance `0x92e49c0' has no handler with id `3269'

** (tsclient:22226): WARNING **: 
ERROR: 192.168.0.102: unable to connect



** (tsclient:22226): WARNING **: 
ERROR: 192.168.0.102: unable to connect



(tsclient:22226): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.20.1/gobject/gsignal.c:2387: instance `0x9354aa0' has no handler with id `4853'
23/06/2009 00&#26102;25&#20998;12&#31186; [IPv6] Got connection from client ::ffff:192.168.0.102
23/06/2009 00&#26102;25&#20998;12&#31186;   other clients:
23/06/2009 00&#26102;25&#20998;13&#31186; Client Protocol Version 3.7
23/06/2009 00&#26102;25&#20998;13&#31186; Advertising security type 18
23/06/2009 00&#26102;25&#20998;13&#31186; Advertising security type 1
23/06/2009 00&#26102;25&#20998;13&#31186; Client returned security type 18
23/06/2009 00&#26102;25&#20998;21&#31186; Advertising authentication type 1
23/06/2009 00&#26102;25&#20998;21&#31186; Client returned authentication type 1
23/06/2009 00&#26102;25&#20998;52&#31186; Client ::ffff:192.168.0.102 gone
23/06/2009 00&#26102;25&#20998;52&#31186; Statistics:
23/06/2009 00&#26102;25&#20998;52&#31186;   framebuffer updates 0, rectangles 0, bytes 0
** (update-notifier:4245): DEBUG: /usr/lib/update-notifier/apt-check returned 239 (security: 55)
Loading simple Config module ...
Creating backend ...
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSLoading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.7

** (update-notifier:4245): DEBUG: /usr/lib/update-notifier/apt-check returned 239 (security: 55)
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.7

gpgv: &#20110; 2009&#24180;04&#26376;20&#26085; &#26143;&#26399;&#19968; 22&#26102;02&#20998;22&#31186; CST &#21019;&#24314;&#30340;&#31614;&#21517;&#65292;&#20351;&#29992; DSA&#65292;&#38053;&#21273;&#21495; FBB75451
gpgv: &#23436;&#22909;&#30340;&#31614;&#21517;&#65292;&#26469;&#33258;&#20110;“Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>”
** (update-notifier:4245): DEBUG: /usr/lib/update-notifier/apt-check returned 236 (security: 61)
** (update-notifier:4245): DEBUG: /usr/lib/update-notifier/apt-check returned 236 (security: 61)

```

---

