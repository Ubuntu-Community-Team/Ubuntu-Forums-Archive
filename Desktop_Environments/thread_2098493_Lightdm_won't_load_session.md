---
title: "Lightdm won't load session"
date: 2012-12-26
forum: Desktop Environments
---

### Post by benzejaa on 2012-12-26
So this isn't strictly an ubuntu post...I'm actually trying to get this running under Arch Linux...but it's a problem with lightdm and the unity-greeter, so I thought I might post over here as well in case someone here has an idea to the solution of my problem.  I'm a bit stuck.

So lightdm is installed and it starts up normally, but there is no gear available to choose session type, and logging in causes the DM to just restart and go back to the logon page.

I was able to use lightdm and lightdm-gtk-greeter successfully.  Also, running startx from another tty successfully starts my session (in my case, xmonad).  I've attached my configuration files and log files, in case anyone can make heads or tails of them.

File dump follows!

Here's my etc/lightdm/lightdm.conf:

```

#
# General configuration
#
# start-default-seat = True to always start one seat if none are defined in the configuration
# greeter-user = User to run greeter as
# minimum-display-number = Minimum display number to use for X servers
# minimum-vt = First VT to run displays on
# lock-memory = True to prevent memory from being paged to disk
# user-authority-in-system-dir = True if session authority should be in the system location
# guest-account-script = Script to be run to setup guest account
# log-directory = Directory to log information to
# run-directory = Directory to put running state in
# cache-directory = Directory to cache to
# xsessions-directory = Directory to find X sessions
# remote-sessions-directory = Directory to find remote sessions
# xgreeters-directory = Directory to find X greeters
#

[LightDM]
#start-default-seat=true
#greeter-user=lightdm
#minimum-display-number=0
#minimum-vt=7
#lock-memory=true
#user-authority-in-system-dir=false
#guest-account-script=guest-account
#log-directory=/var/log/lightdm
#run-directory=/var/run/lightdm
#cache-directory=/var/cache/lightdm
xsessions-directory=/usr/share/xsessions
#remote-sessions-directory=/usr/share/lightdm/remote-sessions
#xgreeters-directory=/usr/share/xgreeters

#
# Seat defaults
#
# type = Seat type (xlocal, xremote)
# xserver-command = X server command to run (can also contain arguments e.g. X -special-option)
# xserver-layout = Layout to pass to X server
# xserver-config = Config file to pass to X server
# xserver-allow-tcp = True if TCP/IP connections are allowed to this X server
# xdmcp-manager = XDMCP manager to connect to (implies xserver-allow-tcp=true)
# xdmcp-port = XDMCP UDP/IP port to communicate on
# xdmcp-key = Authentication key to use for XDM-AUTHENTICATION-1 (stored in keys.conf)
# greeter-session = Session to load for greeter
# greeter-hide-users = True to hide the user list
# greeter-allow-guest = True if the greeter should show a guest login option
# greeter-show-manual-login = True if the greeter should offer a manual login option
# greeter-show-remote-login = True if the greeter should offer a remote login option
# user-session = Session to load for users
# allow-guest = True if guest login is allowed
# guest-session = Session to load for guests (overrides user-session)
# session-wrapper = Wrapper script to run session with
# display-setup-script = Script to run when starting a greeter session (runs as root)
# greeter-setup-script = Script to run when starting a greeter (runs as root)
# session-setup-script = Script to run when starting a user session (runs as root)
# session-cleanup-script = Script to run when quitting a user session (runs as root)
# autologin-guest = True to log in as guest by default
# autologin-user = User to log in with by default (overrides autologin-guest)
# autologin-user-timeout = Number of seconds to wait before loading default user
# autologin-session = Session to load for automatic login (overrides user-session)
# exit-on-failure = True if the daemon should exit if this seat fails
#

[SeatDefaults]
type=xlocal
xserver-command=X
#xserver-layout=
#xserver-config=
#xserver-allow-tcp=false
#xdmcp-manager=
#xdmcp-port=177
#xdmcp-key=
#greeter-session=lightdm-unity-greeter
#greeter-hide-users=false
#greeter-allow-guest=true
#greeter-show-manual-login=false
#greeter-show-remote-login=true
user-session=XMonad
#allow-guest=true
#guest-session=UNIMPLEMENTED
#session-wrapper=lightdm-session
#display-setup-script=
#greeter-setup-script=
#session-setup-script=
#session-cleanup-script=
#autologin-guest=false
#autologin-user=
#autologin-user-timeout=0
#autologin-session=UNIMPLEMENTED
#exit-on-failure=false

#
# Seat configuration
#
# Each seat must start with "Seat:".
# Uses settings from [SeatDefaults], any of these can be overriden by setting them in this section.
#
#[Seat:0]

#
# XDMCP Server configuration
#
# enabled = True if XDMCP connections should be allowed
# port = UDP/IP port to listen for connections on
# key = Authentication key to use for XDM-AUTHENTICATION-1 or blank to not use authentication (stored in keys.conf)
#
# The authentication key is a 56 bit DES key specified in hex as 0xnnnnnnnnnnnnnn.  Alternatively
# it can be a word and the first 7 characters are used as the key.
#
greeter-session=unity-greeter

[XDMCPServer]
#enabled=false
#port=177
#key=

#
# VNC Server configuration
#
# enabled = True if VNC connections should be allowed
# port = TCP/IP port to listen for connections on
#

[VNCServer]
#enabled=false
#port=5900
#width=1024
#height=768
#depth=8

```My contents of /usr/share/xsessions:

```

$ ls /usr/share/xsessions
xmonad.desktop

```/usr/share/xsessions/xmonad.desktop
```

[Desktop Entry]
Encoding=UTF-8
Name=XMonad
Comment=Lightweight tiling window manager
Exec=xmonad
Icon=xmonad.png
Type=XSession

```And the log files, after boot and one log on attempt:

/var/log/lightdm/lightdm.log
```

[+0.03s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.03s] DEBUG: Starting Light Display Manager 1.4.0, UID=0 PID=355
[+0.03s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.03s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.27s] DEBUG: Registered seat module xlocal
[+0.27s] DEBUG: Registered seat module xremote
[+0.27s] DEBUG: Adding default seat
[+0.27s] DEBUG: Starting seat
[+0.27s] DEBUG: Starting new display for greeter
[+0.27s] DEBUG: Starting local X display
[+0.31s] DEBUG: Could not run plymouth --ping: Failed to execute child process "plymouth" (No such file or directory)
[+0.31s] DEBUG: Using VT 7
[+0.31s] DEBUG: Activating VT 7
[+0.36s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.43s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.43s] DEBUG: Launching X Server
[+0.43s] DEBUG: Launching process 368: /usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.44s] DEBUG: Waiting for ready signal from X server :0
[+0.44s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.44s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+2.46s] DEBUG: Got signal 10 from process 368
[+2.46s] DEBUG: Got signal from X server :0
[+2.46s] DEBUG: Connecting to XServer :0
[+2.51s] DEBUG: Starting greeter
[+2.51s] DEBUG: Started session 387 with service 'lightdm-greeter', username 'lightdm'
[+3.33s] DEBUG: Session 387 authentication complete with return value 0: Success
[+3.33s] DEBUG: Greeter authorized
[+3.33s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+3.38s] DEBUG: Session 387 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+4.53s] DEBUG: Greeter connected version=1.4.0
[+4.53s] DEBUG: Greeter connected, display is ready
[+4.53s] DEBUG: New display ready, switching to it
[+4.53s] DEBUG: Activating VT 7
[+5.34s] DEBUG: Greeter start authentication for jabenze
[+5.34s] DEBUG: Started session 424 with service 'lightdm', username 'jabenze'
[+5.36s] DEBUG: Greeter start authentication for jabenze
[+5.36s] DEBUG: Session 424: Sending SIGTERM
[+5.36s] DEBUG: Started session 426 with service 'lightdm', username 'jabenze'
[+5.36s] DEBUG: Session 424 terminated with signal 15
[+5.36s] DEBUG: Session 424 failed during authentication
[+5.39s] DEBUG: Session 426 got 1 message(s) from PAM
[+5.39s] DEBUG: Prompt greeter with 1 message(s)
[+13.53s] DEBUG: Continue authentication
[+13.55s] DEBUG: Session 426 authentication complete with return value 0: Success
[+13.55s] DEBUG: Authenticate result for user jabenze: Success
[+13.56s] DEBUG: User jabenze authorized
[+13.56s] DEBUG: Greeter requests session ubuntu
[+13.56s] DEBUG: Using session ubuntu
[+13.56s] DEBUG: Stopping greeter
[+13.56s] DEBUG: Session 387: Sending SIGTERM
[+13.59s] DEBUG: Greeter closed communication channel
[+13.59s] DEBUG: Session 387 exited with return value 0
[+13.59s] DEBUG: Greeter quit
[+13.60s] DEBUG: Dropping privileges to uid 1000
[+13.60s] DEBUG: Calling setresgid
[+13.60s] DEBUG: Calling setresuid
[+13.62s] DEBUG: Restoring privileges
[+13.62s] DEBUG: Calling setresuid
[+13.62s] DEBUG: Calling setresgid
[+13.63s] DEBUG: Dropping privileges to uid 1000
[+13.63s] DEBUG: Calling setresgid
[+13.63s] DEBUG: Calling setresuid
[+13.63s] DEBUG: Writing /home/jabenze/.dmrc
[+13.70s] DEBUG: Restoring privileges
[+13.70s] DEBUG: Calling setresuid
[+13.70s] DEBUG: Calling setresgid
[+13.73s] DEBUG: Failed to load session file /usr/share/xsessions/ubuntu.desktop: No such file or directory
[+13.73s] DEBUG: Failed to start greeter
[+13.73s] DEBUG: Stopping display
[+13.73s] DEBUG: Session 426: Sending SIGTERM
[+13.73s] DEBUG: Session 426 terminated with signal 15
[+13.73s] DEBUG: User session quit
[+13.73s] DEBUG: Sending signal 15 to process 368
[+14.28s] DEBUG: Process 368 exited with return value 0
[+14.28s] DEBUG: X server stopped
[+14.28s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+14.28s] DEBUG: Releasing VT 7
[+14.28s] DEBUG: Display server stopped
[+14.28s] DEBUG: Display stopped
[+14.28s] DEBUG: Active display stopped, switching to greeter
[+14.28s] DEBUG: Switching to greeter
[+14.28s] DEBUG: Starting new display for greeter
[+14.28s] DEBUG: Starting local X display
[+14.28s] DEBUG: Using VT 7
[+14.28s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+14.28s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+14.28s] DEBUG: Launching X Server
[+14.28s] DEBUG: Launching process 463: /usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+14.28s] DEBUG: Waiting for ready signal from X server :0
[+14.88s] DEBUG: Got signal 10 from process 463
[+14.88s] DEBUG: Got signal from X server :0
[+14.88s] DEBUG: Connecting to XServer :0
[+14.88s] DEBUG: Starting greeter
[+14.88s] DEBUG: Started session 468 with service 'lightdm-greeter', username 'lightdm'
[+14.90s] DEBUG: Session 468 authentication complete with return value 0: Success
[+14.90s] DEBUG: Greeter authorized
[+14.90s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+14.90s] DEBUG: Session 468 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+15.01s] DEBUG: Greeter connected version=1.4.0
[+15.01s] DEBUG: Greeter connected, display is ready
[+15.01s] DEBUG: New display ready, switching to it
[+15.01s] DEBUG: Activating VT 7
[+15.01s] DEBUG: Stopping greeter display being switched from
[+15.10s] DEBUG: Greeter start authentication for jabenze
[+15.10s] DEBUG: Started session 500 with service 'lightdm', username 'jabenze'
[+15.11s] DEBUG: Session 500 got 1 message(s) from PAM
[+15.11s] DEBUG: Prompt greeter with 1 message(s)
[+15.15s] DEBUG: Greeter start authentication for jabenze
[+15.15s] DEBUG: Session 500: Sending SIGTERM
[+15.15s] DEBUG: Started session 502 with service 'lightdm', username 'jabenze'
[+15.15s] DEBUG: Session 500 terminated with signal 15
[+15.15s] DEBUG: Session 500 failed during authentication
[+15.15s] DEBUG: Session 502 got 1 message(s) from PAM
[+15.15s] DEBUG: Prompt greeter with 1 message(s)

```/var/log/lightdm/x-0-greeter.log:
```


** (process:468): WARNING **: Failed to open CK session: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.ConsoleKit was not provided by any .service files
Activating service name='org.a11y.atspi.Registry'
[+0.00s] DEBUG: unity-greeter.vala:438: Starting unity-greeter 12.10.4 UID=999 LANG=(null)
[+0.00s] DEBUG: unity-greeter.vala:441: Setting cursor
Successfully activated service 'org.a11y.atspi.Registry'
[+0.00s] DEBUG: unity-greeter.vala:455: Loading command line options
[+0.00s] DEBUG: unity-greeter.vala:483: Setting GTK+ settings

** (at-spi2-registryd:490): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (at-spi2-registryd:490): WARNING **: Unable to register client with session manager
[+0.04s] DEBUG: unity-greeter.vala:506: Creating Unity Greeter
[+0.04s] DEBUG: unity-greeter.vala:55: Creating background surface
[+0.04s] DEBUG: Connecting to display manager...
[+0.04s] DEBUG: Wrote 17 bytes to daemon
[+0.04s] DEBUG: Read 8 bytes from daemon
[+0.04s] DEBUG: Read 149 bytes from daemon
[+0.04s] DEBUG: Connected version=1.4.0 default-session=XMonad show-manual-login=false hide-users=false has-guest-account=true show-remote-login=true
[+0.06s] DEBUG: menubar.vala:342: LANG=(null) LANGUAGE=(null)
[+0.06s] WARNING: File '/usr/lib/indicators3/7/libsession.so' does not exist.
[+0.06s] WARNING: File '/usr/lib/indicators3/7/libdatetime.so' does not exist.
[+0.06s] WARNING: File '/usr/lib/indicators3/7/libpower.so' does not exist.
[+0.06s] WARNING: File '/usr/lib/indicators3/7/libsoundmenu.so' does not exist.
[+0.06s] WARNING: File '/usr/lib/indicators3/7/libapplication.so' does not exist.
[+0.06s] DEBUG: menubar.vala:360: LANG=(null) LANGUAGE=(null)
[+0.07s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.07s] DEBUG: Loading user /org/freedesktop/Accounts/User1000
[+0.08s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+0.08s] DEBUG: user-list.vala:950: Adding/updating user jabenze ()
[+0.08s] WARNING: Could not get accounts property XKeyboardLayouts
[+0.08s] WARNING: Could not get accounts property XHasMessages
[+0.08s] CRITICAL: g_variant_get_type: assertion `value != NULL' failed
[+0.08s] CRITICAL: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed
[+0.08s] CRITICAL: g_variant_get_type_string: assertion `value != NULL' failed
[+0.08s] WARNING: Unexpected accounts property type for XHasMessages: (null)
[+0.08s] CRITICAL: g_variant_unref: assertion `value != NULL' failed
[+0.08s] WARNING: Could not get accounts property XKeyboardLayouts
[+0.08s] WARNING: Could not get accounts property XHasMessages
[+0.08s] CRITICAL: g_variant_get_type: assertion `value != NULL' failed
[+0.08s] CRITICAL: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed
[+0.08s] CRITICAL: g_variant_get_type_string: assertion `value != NULL' failed
[+0.08s] WARNING: Unexpected accounts property type for XHasMessages: (null)
[+0.08s] CRITICAL: g_variant_unref: assertion `value != NULL' failed
[+0.08s] WARNING: Could not get accounts property XKeyboardLayouts
[+0.08s] WARNING: Could not get accounts property XHasMessages
[+0.08s] CRITICAL: g_variant_get_type: assertion `value != NULL' failed
[+0.08s] CRITICAL: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed
[+0.08s] CRITICAL: g_variant_get_type_string: assertion `value != NULL' failed
[+0.08s] WARNING: Unexpected accounts property type for XHasMessages: (null)
[+0.08s] CRITICAL: g_variant_unref: assertion `value != NULL' failed
[+0.08s] DEBUG: user-list.vala:932: Adding guest account entry
[+0.13s] DEBUG: Loaded session /usr/share/xsessions/xmonad.desktop (XMonad, Lightweight tiling window manager)
[+0.13s] WARNING: Failed to open sessions directory: Error opening directory '/usr/share/lightdm/remote-sessions': No such file or directory
[+0.13s] DEBUG: Starting authentication for user jabenze...
[+0.13s] DEBUG: Wrote 23 bytes to daemon
[+0.18s] DEBUG: Starting authentication for user jabenze...
[+0.18s] DEBUG: Wrote 23 bytes to daemon
[+0.18s] DEBUG: main-window.vala:176: Screen is 3840x1080 pixels
[+0.18s] DEBUG: main-window.vala:182: Monitor 0 is 1920x1080 pixels at 0,0
[+0.18s] DEBUG: main-window.vala:182: Monitor 1 is 1920x1080 pixels at 1920,0
[+0.18s] DEBUG: unity-greeter.vala:509: Showing greeter
[+0.18s] DEBUG: unity-greeter.vala:198: Showing main window
[+0.21s] DEBUG: background.vala:470: Regenerating backgrounds
[+0.21s] DEBUG: background.vala:68: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 1920x1080
[+0.21s] WARNING: unity-greeter.vala:523: Error starting nm-applet: Failed to execute child process "nm-applet" (No such file or directory)
[+0.21s] DEBUG: unity-greeter.vala:527: Starting main loop
[+0.21s] DEBUG: Read 8 bytes from daemon
[+0.21s] DEBUG: Read 37 bytes from daemon
[+0.21s] DEBUG: Ignoring prompt authentication with invalid sequence number 1
[+0.21s] DEBUG: settings-daemon.vala:97: Could not start gnome-settings-daemon over DBus: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SettingsDaemon was not provided by any .service files
[+0.27s] DEBUG: Setting keyboard layout to 'us'
[+0.29s] DEBUG: Read 8 bytes from daemon
[+0.29s] DEBUG: Read 37 bytes from daemon
[+0.29s] DEBUG: Prompt user with 1 message(s)
[+0.32s] DEBUG: unity-greeter.vala:181: starting system-ready sound
[+0.38s] DEBUG: background.vala:117: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete

```/var/log/lightdm/x-0.log
```


X.Org X Server 1.13.1
Release Date: 2012-12-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.7.0-1-ARCH x86_64 
Current Operating System: Linux frankie 3.6.10-1-ARCH #1 SMP PREEMPT Tue Dec 11 09:40:17 CET 2012 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-linux root=UUID=51606072-17ca-431e-a2bf-ba739d1cfeb1 ro quiet
Build Date: 16 December 2012  04:45:14PM
 
Current version of pixman: 0.28.2
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 26 13:36:33 2012
(==) Using config directory: "/etc/X11/xorg.conf.d"
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
Loading extension NV-GLX
Loading extension NV-CONTROL
Loading extension XINERAMA

```

---

### Post by dgharmon on 2012-12-26
> **benzejaa said:**
> So lightdm is installed and it starts up normally, but there is no gear available to choose session type, and logging in causes the DM to just restart and go back to the logon page

Boot into single user mode and delete the contents of /tmp ...

---

### Post by benzejaa on 2012-12-26
Hi dgharmon:

I gave this a shot, but it does not seem to change anything.  Thanks for the idea though!

---

