---
title: "Mysterious GDM crashes"
date: 2007-05-03
forum: Desktop Environments
---

### Post by Jujimufu on 2007-05-03
I just got Beryl and XGL working recently. Unfortunately I'm suffering from sporadic crashes.

The crash kicks me out of X, and gdm instantly restarts bringing me back into the login screen. Then I log back in and it's fine until it repeats. Certain programs seem to trigger it. GAIM always makes it crash. It's never at the same rate, sometimes it'll crash fast, other times I can have a conversation for 5 or 10 minutes before it crashes. Gedit makes it crash it seems, and Audacious I believe has made it crash once or twice.

Here is a relevant portion I found in /var/log/messages, notice that the system didn't write any messages to the log for two minutes, then a series of events took place that made it crash. 

> 
**Apr 27 22:20:01** localhost cron[5976]: (root) CMD (test -x /usr/sbin/run-crons && /usr/sbin/run-crons )
[COLOR="Red"]**Apr 27 22:22:11** localhost gdm[5545]: slave_waitpid: done_waiting[/COLOR]
Apr 27 22:22:11 localhost gdm[5545]: Session: start_time: 1177726787 end_time: 1177726931
Apr 27 22:22:11 localhost gdm[5545]: Sending SESSPID == 0 for slave 5545
Apr 27 22:22:11 localhost gdm[5533]: Handling message: 'SESSPID 5545 0'
Apr 27 22:22:11 localhost gdm[5533]: Got SESSPID == 0
Apr 27 22:22:11 localhost [fglrx:firegl_rmmap] *ERROR* map 0xf7149170 still in use (map_count=1)
Apr 27 22:22:11 localhost [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xf7149160 still mapped (user_handle = 0x0000a000)
Apr 27 22:22:11 localhost [fglrx:firegl_rmmap] *ERROR* map 0xf71491f0 still in use (map_count=1)
Apr 27 22:22:11 localhost [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xf71491e0 still mapped (user_handle = 0x0000b000)
Apr 27 22:22:11 localhost [fglrx:firegl_rmmap] *ERROR* map 0xf7925350 still in use (map_count=1)
Apr 27 22:22:11 localhost [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xf7925340 still mapped (user_handle = 0x00007000)
Apr 27 22:22:11 localhost [fglrx:firegl_rmmap] *ERROR* map 0xf7149df0 still in use (map_count=1)
Apr 27 22:22:11 localhost [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xf7149de0 still mapped (user_handle = 0x00006000)
Apr 27 22:22:11 localhost [fglrx:firegl_rmmap] *ERROR* map 0xf7149d70 still in use (map_count=1)
Apr 27 22:22:11 localhost [fglrx:firegl_free_buffer_queue] *ERROR* buffer queue 0xf7149d60 still mapped (user_handle = 0x00005000)
Apr 27 22:22:11 localhost gdm[5533]: Handling message: 'XPID 5545 0'
Apr 27 22:22:11 localhost gdm[5533]: Got XPID == 0
Apr 27 22:22:20 localhost login(pam_unix)[5779]: session opened for user hawaii by (uid=0)
Apr 27 22:22:21 localhost gdm[5545]: gdm_slave_session_stop: hawaii on :1
[COLOR="Red"]Apr 27 22:22:21 localhost gdm[5545]: Fatal X error detected. Ignoring same during session shut down.[/COLOR]
Apr 27 22:22:21 localhost gdm[5545]: gdm_slave_session_stop: back here from xioerror
Apr 27 22:22:21 localhost gdm[5545]: gdm_slave_session_stop: Running post session script
Apr 27 22:22:21 localhost gdm[5545]: gdm_auth_user_remove: Removing cookie from /home/hawaii/.Xauthority (0)
Apr 27 22:22:21 localhost gdm[5545]: gdm_auth_purge: :1
Apr 27 22:22:21 localhost gdm[5545]: Running gdm_verify_cleanup and pamh != NULL
Apr 27 22:22:21 localhost gdm[5545]: Running pam_close_session
Apr 27 22:22:21 localhost gdm(pam_unix)[5545]: session closed for user hawaii
Apr 27 22:22:21 localhost gdm[5545]: Running pam_setcred with PAM_DELETE_CRED
Apr 27 22:22:21 localhost gdm[5533]: Handling message: 'LOGGED_IN 5545 0'
Apr 27 22:22:21 localhost gdm[5533]: Got logged in == FALSE
[COLOR="Red"]Apr 27 22:22:21 localhost gdm[5545]: gdm_slave_session_start: Session ended OK (now all finished)[/COLOR]
Apr 27 22:22:21 localhost gdm[5545]: Sending LOGGED_IN == 0 for slave 5545
Apr 27 22:22:21 localhost gdm[5545]: Sending LOGIN == <secret> for slave 5545
Apr 27 22:22:21 localhost gdm[5533]: Handling message: 'LOGIN 5545 '
Apr 27 22:22:21 localhost gdm[5533]: Got LOGIN ==
Apr 27 22:22:21 localhost gdm[5545]: gdm_slave_start: Reinitializing things
Apr 27 22:22:21 localhost gdm[5545]: gdm_auth_secure_display: Setting up access for :1
Apr 27 22:22:21 localhost gdm[5545]: gdm_auth_secure_display: Setting up access
Apr 27 22:22:21 localhost gdm[5545]: gdm_auth_secure_display: Setting up access for :1 - 1 entries
Apr 27 22:22:21 localhost gdm[5545]: Sending COOKIE == <secret> for slave 5545
Apr 27 22:22:21 localhost gdm[5533]: Handling message: 'COOKIE 5545 a4...'
Apr 27 22:22:21 localhost gdm[5533]: Got COOKIE == <secret>
Apr 27 22:22:21 localhost gdm[5545]: Sending AUTHFILE == <secret> for slave 5545
Apr 27 22:22:21 localhost gdm[5533]: Handling message: 'AUTHFILE 5545 /var/gdm/:1.Xauth'
Apr 27 22:22:21 localhost gdm[5533]: Got AUTHFILE == /var/gdm/:1.Xauth
Apr 27 22:22:21 localhost gdm[5545]: Error reinitilizing server
Apr 27 22:22:21 localhost gdm[5545]: gdm_slave_quick_exit: Will kill everything from the display
Apr 27 22:22:21 localhost gdm[5545]: gdm_slave_quick_exit: Killed everything from the display
Apr 27 22:22:21 localhost gdm[5533]: mainloop_sig_callback: Got signal 17
Apr 27 22:22:21 localhost gdm[5533]: gdm_cleanup_children: child 5545 returned 2
Apr 27 22:22:21 localhost gdm[5533]: gdm_child_action: In remanage
Apr 27 22:22:21 localhost gdm[5533]: gdm_display_manage: Managing :1
Apr 27 22:22:21 localhost gdm[5533]: loop check: last_start 1177726766, last_loop 1177726766, now: 1177726941, retry_count: 1
Apr 27 22:22:21 localhost gdm[5533]: Resetting counts for loop of death detection, 90 seconds elapsed since loop started or session lasted more then 30 seconds.
Apr 27 22:22:21 localhost gdm[5533]: gdm_display_manage: Forked slave: 6055
Apr 27 22:22:21 localhost gdm[6055]: gdm_slave_start: Starting slave process for :1
Apr 27 22:22:21 localhost gdm[6055]: gdm_slave_start: Loop Thingie
Apr 27 22:22:21 localhost gdm[6055]: gdm_slave_run: Sleeping 1 seconds before server start
Apr 27 22:22:22 localhost gdm[6055]: Sending VT_NUM == -1 for slave 6055
Apr 27 22:22:22 localhost gdm[5533]: Handling message: 'VT_NUM 6055 -1'
Apr 27 22:22:22 localhost gdm[5533]: Got VT_NUM == -1
Apr 27 22:22:22 localhost gdm[6055]: gdm_server_start: :1
Apr 27 22:22:22 localhost gdm[6055]: gdm_auth_secure_display: Setting up access for :1
Apr 27 22:22:22 localhost gdm[6055]: gdm_auth_secure_display: Setting up access
Apr 27 22:22:22 localhost gdm[6055]: gdm_auth_secure_display: Setting up access for :1 - 1 entries
Apr 27 22:22:22 localhost gdm[6055]: Sending COOKIE == <secret> for slave 6055
Apr 27 22:22:22 localhost gdm[5533]: Handling message: 'COOKIE 6055 8e...'
Apr 27 22:22:22 localhost gdm[5533]: Got COOKIE == <secret>
Apr 27 22:22:22 localhost gdm[6055]: Sending AUTHFILE == <secret> for slave 6055
Apr 27 22:22:22 localhost gdm[5533]: Handling message: 'AUTHFILE 6055 /var/gdm/:1.Xauth'
Apr 27 22:22:22 localhost gdm[5533]: Got AUTHFILE == /var/gdm/:1.Xauth
Apr 27 22:22:22 localhost gdm[6055]: gdm_server_spawn: Forked server on pid 6056
Apr 27 22:22:22 localhost gdm[6055]: do_server_wait: Before mainloop waiting for server
Apr 27 22:22:22 localhost gdm[6056]: gdm_server_spawn: '/usr/bin/Xgl :1 :1 -ac -accel glx:pbuffer -accel xv:pbuffer -auth /var/gdm/:1.Xauth -nolisten tcp vt7'
Apr 27 22:22:26 localhost [fglrx] Internal AGP support requested, but kernel AGP support active.
Apr 27 22:22:26 localhost [fglrx] Have to use kernel AGP support to avoid conflicts.
Apr 27 22:22:26 localhost [fglrx] AGP detected, AgpState = 0x1f00421b (hardware caps of chipset)
Apr 27 22:22:26 localhost agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Apr 27 22:22:26 localhost agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Apr 27 22:22:26 localhost agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
Apr 27 22:22:26 localhost [fglrx] AGP enabled, AgpCommand = 0x1f004312 (selected caps)
Apr 27 22:22:26 localhost [fglrx] total GART = 134217728
Apr 27 22:22:26 localhost [fglrx] free GART = 118222848
Apr 27 22:22:26 localhost [fglrx] max single GART = 118222848
Apr 27 22:22:26 localhost [fglrx] total LFB = 134217728
Apr 27 22:22:26 localhost [fglrx] free LFB = 116387840
Apr 27 22:22:26 localhost [fglrx] max single LFB = 116387840
Apr 27 22:22:26 localhost [fglrx] total Inv = 0
Apr 27 22:22:26 localhost [fglrx] free Inv = 0
Apr 27 22:22:26 localhost [fglrx] max single Inv = 0
Apr 27 22:22:26 localhost [fglrx] total TIM = 0
Apr 27 22:22:29 localhost gdm[6055]: gdm_server_start: After mainloop waiting for server
Apr 27 22:22:29 localhost gdm[6055]: gdm_server_start: Completed :1! 



Here is the result of cat /var/log/Xorg.0.log | grep EE 

> 
(EE) fglrx(0): Hardware has already been locked.
(EE) AIGLX: Screen 0 is not DRI capable


Here is the result of cat /var/log/Xorg.0.log | grep WW 

> 
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) Duplicate core pointer devices. Removing core pointer attribute from "ATI Remote"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed! *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO) *
(WW) fglrx(0): * no 3D acceleration available *
(WW) fglrx(0): ********************************************* *


Is the (0) in front of fglrx indicative of the screen number? Because if so I'm running on screen 1.

Here is my xorg.conf file: 

> 
Section "Module"

Load "dbe"

SubSection "extmod"
Option "omit xfree86-dga"
EndSubSection

Load "freetype"
Load "glx"
Load "dri"

EndSection

Section "Files"

FontPath "/usr/share/fonts/misc/"
FontPath "/usr/share/fonts/Type1/"
FontPath "/usr/share/fonts/100dpi/"
FontPath "/usr/share/fonts/75dpi/"

EndSection

Section "ServerFlags"

EndSection

Section "InputDevice"

Identifier "Keyboard1"
Driver "kbd"
Option "AutoRepeat" "500 30"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"

EndSection

Section "InputDevice"

Identifier "Mouse1"
Driver "mouse"
Option "Protocol" "Auto" # Auto detect
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5 6 7"

EndSection

Section "Monitor"

Identifier "A90f+"
HorizSync 30-86
VertRefresh 50-180

EndSection

Section "Device"
Identifier "Standard VGA"
VendorName "Unknown"
BoardName "Unknown"
Driver "fglrx"
EndSection

Section "Device"
Identifier "Ati Radeon 9800"
Driver "fglrx"
EndSection

Section "Screen"
Identifier "Screen 1"
Device "Ati Radeon 9800"
Monitor "A90f+"
DefaultDepth 24

Subsection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
ViewPort 0 0
EndSubsection
Subsection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
ViewPort 0 0
EndSubsection
Subsection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
ViewPort 0 0
EndSubsection
EndSection

Section "Screen"
Identifier "Screen 0"
Device "Ati Radeon 9800"
Monitor "A90f+"
DefaultDepth 24

Subsection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
ViewPort 0 0
EndSubsection
Subsection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
ViewPort 0 0
EndSubsection
Subsection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
ViewPort 0 0
EndSubsection
EndSection

Section "ServerLayout"
Identifier "Simple Layout"
Option "AIGLX" "False"
Screen "Screen 1"
InputDevice "Mouse1" "CorePointer"
InputDevice "Keyboard1" "CoreKeyboard"
# InputDevice "ATI Remote" "CorePointer"

EndSection

Section "DRI"
Group "video"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "false"
EndSection 


More from /var/log/messages 

> 
May 1 00:00:01 localhost cron[6277]: (root) CMD (test -x /usr/sbin/run-crons && /usr/sbin/run-crons )
May 1 00:00:01 localhost cron[6279]: (root) CMD (rm -f /var/spool/cron/lastrun/cron.hourly)
May 1 00:10:01 localhost cron[6291]: (root) CMD (test -x /usr/sbin/run-crons && /usr/sbin/run-crons )
May 1 00:20:01 localhost cron[6306]: (root) CMD (test -x /usr/sbin/run-crons && /usr/sbin/run-crons )
May 1 00:30:01 localhost cron[6318]: (root) CMD (test -x /usr/sbin/run-crons && /usr/sbin/run-crons )
May 1 00:33:33 localhost gdm[5536]: Handling message: 'XPID 5548 0'
May 1 00:33:33 localhost gdm[5536]: Got XPID == 0
May 1 00:33:33 localhost gdm[5536]: Handling message: 'SESSPID 5548 0'
May 1 00:33:33 localhost gdm[5536]: Got SESSPID == 0
May 1 00:33:33 localhost (hawaii-5827): Received signal 15, shutting down cleanly
May 1 00:33:33 localhost (hawaii-5827): Exiting
May 1 00:33:33 localhost gdm[5548]: slave_waitpid: done_waiting
May 1 00:33:33 localhost gdm[5548]: Session: start_time: 1177988825 end_time: 1177994013
May 1 00:33:33 localhost gdm[5548]: Sending SESSPID == 0 for slave 5548
May 1 00:33:33 localhost gdm[5536]: Handling message: 'SESSPID 5548 0'
May 1 00:33:33 localhost gdm[5536]: Got SESSPID == 0
May 1 00:33:33 localhost gdm[5548]: gdm_slave_session_stop: hawaii on :1
May 1 00:33:33 localhost gdm[5548]: Fatal X error detected. Ignoring same during session shut down.
May 1 00:33:33 localhost gdm[5548]: gdm_slave_session_stop: back here from xioerror
May 1 00:33:33 localhost gdm[5548]: gdm_slave_session_stop: Running post session script 


I'd be happy to give any more information if someone thinks they can help me! I tried to provide as much as I could. I'd appreciate it immensely, I've been suffering with this for a week now!! :wink:

One final note: XGL and Beryl seem to be working fine otherwise, faaaaaast beryl with full features. But the crashes?! Frequent and ruining. :(

---

### Post by Jujimufu on 2007-05-04
anyone? :-k

---

