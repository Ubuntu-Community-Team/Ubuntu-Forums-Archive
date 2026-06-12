---
title: "x11vnc crashes when starting a VM in Virtualbox on Host System"
date: 2009-01-05
forum: Desktop Environments
---

### Post by irvin on 2009-01-05
Hallo

I tried a lot, read a lot but couldn't fix this Problem.

Host System:
- Ubuntu 8.10 64-bit
- openssh-server
- x11vnc 0.9.3
- Virtualbox 2.1.0
at this moment the system has a mouse, keyboard and a tft display connected.

Now I connect from windows via putty and tightvnc viewer.
I start virtualbox and start a VM (Virtual Machine) or even start a setup for a new VM - Everything works fine !!!

As I want to use this server in a server housing area, so there is no mouse, keyboard oder display connected.
So, I disconnected these 3 things and started the Host.

Then i connect from windows via putty, everythings seems to be great ;-)

I start Virtualbox, ok ! But when i start a VM oder even a setup for a new VM the VNC connection crashes immediately !

When I try to reconnect I get the ubuntu login screen and have to log on again. Nothing of the Programs that ran is still running, it's like a new reboot. when i now start virtualbox i see that my VM crashed (shutdown failed or something like this).

I tried this with Ubuntu 8.04 and 8.10 (both 64-bit) and x11vnc (0.9.3).

I tried to make static resolutions for the non existing display, but nothing worked. I read about the Edid Information which Ubuntu tries to finsd after rebooting, but when there's no display ? It should be something like this, but I don't know.
I wanted to make a static resolution for the VNC, but this seems not to be possible.

I tried to build a newer x11vnc for hours but I'm not the man for this. tried checkinstall, install a lot of stuff but there's no result for me. Only errors. I read a lot of Karl Runges site, but as I'm not a specialist on Linux it's a bit difficult for me.

Also I read about the xorg.conf file and that it's not more that important in 8.04 and they changed lots of stuff into "10-x11-input.fdi" file in 8.10.

Puuuuhhh...
And after switching to 8.10 I had the x11vnc Problems with the "-nofixes" it seemed like the problems like to grow ;-)

I Hope someone has an idea
Thanx

---

### Post by albinootje on 2009-01-05
> **irvin said:**
> 
I start Virtualbox, ok ! But when i start a VM oder even a setup for a new VM the VNC connection crashes immediately !


FYI. I've run a VirtualBox VM via a remote FreeNX desktop several times without any problems.

---

### Post by irvin on 2009-01-05
> **albinootje said:**
> FYI. I've run a VirtualBox VM via a remote FreeNX desktop several times without any problems.

Thanx, but as I use x11vnc now for about 2 years with different servers and all working fine, I'd like to stay with a system I know. And I read about Problems with freenx and 64-bit Systems !

Do you use a 64-bit Ubuntu 8.10 Host ?

---

### Post by albinootje on 2009-01-05
> **irvin said:**
> Thanx, but as I use x11vnc now for about 2 years with different servers and all working fine, I'd like to stay with a system I know. And I read about Problems with freenx and 64-bit Systems !

Okay, I hope someone else can help you any further.
> 
Do you use a 64-bit Ubuntu 8.10 Host ?

No, it was 32-bit.
I'm using it as VPS with OpenVZ, and I'm not sure whether OpenVZ on a 32-bit Host can run 64-bit VPS-es.
I'm thinking of installing Ubuntu Hardy or Debian Etch instead of Ubuntu Intrepid because I find the keyboard problems with 8.10 and FreeNX too annoying to deal with.

---

### Post by krunge on 2009-01-05
> **irvin said:**
> 
I Hope someone has an idea
Thanx

Could you post here all of the error messages you get?  x11vnc output, Xorg output, and any other things in /var/log you find that might be useful.

---

### Post by irvin on 2009-01-06
Hallo

I looked for each log file was was updated or newer when the crash was. Because there are sometimes real large, I only post the results of the last minutes.

I have a Problem with the x11vnc.log file cause it will be deleted when I reconnect. I changed the directory from /tmp to /var/log cause I thought it might be deleted only cause it's in the tmp dir but so there's no log file of the crash.

(auth.log)

Jan  6 09:38:07 TEST gdm[4940]: Autolaunch error: X11 initialization failed.
Jan  6 09:38:07 TEST gdm[4940]: )
Jan  6 09:38:52 TEST sudo:     test : TTY=pts/1 ; PWD=/home/test ; USER=root ; COMMAND=/usr/bin/nautilus
Jan  6 09:49:58 TEST gdm[4940]: pam_unix(gdm:session): session closed for user test
Jan  6 09:50:13 TEST gdm[5766]: pam_unix(gdm:session): session opened for user test by (uid=0)
Jan  6 09:50:13 TEST gdm[5766]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Jan  6 09:50:13 TEST gdm[5766]: gnome-keyring-daemon: couldn't lookup keyring component setting: Der Konfigurationsserver konnte nicht kontaktiert werden; mögliche Fehlerquellen sind, dass TCP/IP für ORBit nicht aktiviert ist oder auf Grund eines Systemabsturzes alte NFS-Sperren gesetzt sind. Unter [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) erhalten Sie weitere Informationen (Details -  1: Verbindung zur Sitzung konnte nicht abgerufen werden: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Jan  6 09:50:13 TEST gdm[5766]: Autolaunch error: X11 initialization failed.
Jan  6 09:50:13 TEST gdm[5766]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Der Konfigurationsserver konnte nicht kontaktiert werden; mögliche Fehlerquellen sind, dass TCP/IP für ORBit nicht aktiviert ist oder auf Grund eines Systemabsturzes alte NFS-Sperren gesetzt sind. Unter [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) erhalten Sie weitere Informationen (Details -  1: Verbindung zur Sitzung konnte nicht abgerufen werden: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Jan  6 09:50:13 TEST gdm[5766]: Autolaunch error: X11 initialization failed.
Jan  6 09:50:13 TEST gdm[5766]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Der Konfigurationsserver konnte nicht kontaktiert werden; mögliche Fehlerquellen sind, dass TCP/IP für ORBit nicht aktiviert ist oder auf Grund eines Systemabsturzes alte NFS-Sperren gesetzt sind. Unter [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) erhalten Sie weitere Informationen (Details -  1: Verbindung zur Sitzung konnte nicht abgerufen werden: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Jan  6 09:50:13 TEST gdm[5766]: Autolaunch error: X11 initialization failed.
Jan  6 09:50:13 TEST gdm[5766]: )
Jan  6 09:51:08 TEST sudo:     test : TTY=pts/1 ; PWD=/home/test ; USER=root ; COMMAND=/usr/bin/nautilus

(syslog)

Jan  6 09:49:59 TEST acpid: client connected from 5780[0:0] 
Jan  6 09:49:59 TEST kernel: [  951.535715] [drm] Setting GART location based on new memory map
Jan  6 09:49:59 TEST kernel: [  951.537684] [drm] Loading RS690 Microcode
Jan  6 09:49:59 TEST kernel: [  951.537729] [drm] Num pipes: 1
Jan  6 09:49:59 TEST kernel: [  951.537737] [drm] writeback test succeeded in 1 usecs
Jan  6 09:50:01 TEST gdmgreeter[5793]: Gtk-WARNING: Im Modulpfad »ubuntulooks« konnte keine Themen-Engine gefunden werden, 
Jan  6 09:50:14 TEST pulseaudio[5888]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jan  6 09:50:14 TEST pulseaudio[5890]: pid.c: Stale PID file, overwriting.
Jan  6 09:50:14 TEST pulseaudio[5890]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jan  6 09:50:14 TEST pulseaudio[5890]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jan  6 09:50:15 TEST x-session-manager[5813]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Jan  6 09:50:25 TEST x-session-manager[5813]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Jan  6 09:50:35 TEST x-session-manager[5813]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Jan  6 09:50:35 TEST pulseaudio[5890]: module-x11-xsmp.c: X11 session manager not running.
Jan  6 09:50:35 TEST pulseaudio[5890]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Jan  6 09:50:36 TEST NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 

(daemon.log)

Jan  6 09:49:58 TEST gdm[4940]: WARNING: gdm_slave_xioerror_handler: Schwerwiegender X-Fehler - :0 wird neu gestartet 
Jan  6 09:49:59 TEST acpid: client connected from 5780[0:0] 
Jan  6 09:50:01 TEST gdmgreeter[5793]: Gtk-WARNING: Im Modulpfad »ubuntulooks« konnte keine Themen-Engine gefunden werden, 
Jan  6 09:50:15 TEST x-session-manager[5813]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Jan  6 09:50:25 TEST x-session-manager[5813]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Jan  6 09:50:35 TEST x-session-manager[5813]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Jan  6 09:50:36 TEST NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 

(user.log)

Jan  6 09:49:58 TEST bonobo-activation-server (test-5763): could not associate with desktop session: Failed to connect to socket /tmp/dbus-aHiJEcEhWy: Connection refused
Jan  6 09:50:14 TEST pulseaudio[5888]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jan  6 09:50:14 TEST pulseaudio[5890]: pid.c: Stale PID file, overwriting.
Jan  6 09:50:14 TEST pulseaudio[5890]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jan  6 09:50:14 TEST pulseaudio[5890]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jan  6 09:50:35 TEST pulseaudio[5890]: module-x11-xsmp.c: X11 session manager not running.
Jan  6 09:50:35 TEST pulseaudio[5890]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

(Xorg.0.log)

invalid output device for dac detection
AUDIT: Tue Jan  6 09:50:01 2009: 5780 X: client 10 rejected from local host ( uid=0 gid=0 pid=5795 )
AUDIT: Tue Jan  6 09:50:13 2009: 5780 X: client 10 rejected from local host ( uid=1000 gid=1000 pid=5799 )
AUDIT: Tue Jan  6 09:50:13 2009: 5780 X: client 10 rejected from local host ( uid=1000 gid=1000 pid=5800 )
AUDIT: Tue Jan  6 09:50:13 2009: 5780 X: client 10 rejected from local host ( uid=1000 gid=1000 pid=5801 )
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): I2C device "HDMI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "HDMI-0:ddc2" removed.
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection

(var/log/gdm/0.log)


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux TEST 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan  6 09:49:59 2009
(==) Using config file: "/etc/X11/xorg.conf"
Dac detection success
finished output detect: 0
invalid output device for dac detection
finished output detect: 1
invalid output device for dac detection
finished output detect: 2
(EE) RADEON(0): No connected devices found!
finished all detect
before xf86InitialConfiguration
Dac detection success
(EE) RADEON(0): Using VGA default
in RADEONProbeOutputModes
invalid output device for dac detection
invalid output device for dac detection
after xf86InitialConfiguration
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Output 26 disable success
Output 51 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1152x864 - 1520 895 6
freq: 81620000
best_freq: 81624000
best_feedback_div: 228
best_ref_div: 5
best_post_div: 8
Set CRTC PLL success
Set CRTC Timing success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
Output DAC1 setup success
Output 68 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 26 disable success
Output 51 disable success
Blank CRTC 1 success
Disable CRTC 1 success
Dac detection success
invalid output device for dac detection
invalid output device for dac detection
Dac detection success
invalid output device for dac detection
invalid output device for dac detection
AUDIT: Tue Jan  6 09:50:01 2009: 5780 X: client 10 rejected from local host ( uid=0 gid=0 pid=5795 )
AUDIT: Tue Jan  6 09:50:13 2009: 5780 X: client 10 rejected from local host ( uid=1000 gid=1000 pid=5799 )
AUDIT: Tue Jan  6 09:50:13 2009: 5780 X: client 10 rejected from local host ( uid=1000 gid=1000 pid=5800 )
AUDIT: Tue Jan  6 09:50:13 2009: 5780 X: client 10 rejected from local host ( uid=1000 gid=1000 pid=5801 )
Dac detection success
invalid output device for dac detection
invalid output device for dac detection
Dac detection success
invalid output device for dac detection
invalid output device for dac detection
Dac detection success
invalid output device for dac detection
invalid output device for dac detection
Dac detection success
invalid output device for dac detection
invalid output device for dac detection
Dac detection success
invalid output device for dac detection
invalid output device for dac detection
Dac detection success
invalid output device for dac detection
invalid output device for dac detection
+++++++++++++++++++++
(x11vnc.log)

06/01/2009 10:15:27 passing arg to libvncserver: -rfbauth
06/01/2009 10:15:27 passing arg to libvncserver: /etc/x11vnc.pass
06/01/2009 10:15:27 passing arg to libvncserver: -rfbport
06/01/2009 10:15:27 passing arg to libvncserver: 5900
06/01/2009 10:15:27 x11vnc version: 0.9.3 lastmod: 2007-09-30
06/01/2009 10:15:27 Using X display :0
06/01/2009 10:15:27 
06/01/2009 10:15:27 ------------------ USEFUL INFORMATION ------------------
06/01/2009 10:15:27 X DAMAGE available on display, using it for polling hints.
06/01/2009 10:15:27   To disable this behavior use: '-noxdamage'
06/01/2009 10:15:27 
06/01/2009 10:15:27 Wireframing: -wireframe mode is in effect for window moves.
06/01/2009 10:15:27   If this yields undesired behavior (poor response, painting
06/01/2009 10:15:27   errors, etc) it may be disabled:
06/01/2009 10:15:27    - use '-nowf' to disable wireframing completely.
06/01/2009 10:15:27    - use '-nowcr' to disable the Copy Rectangle after the
06/01/2009 10:15:27      moved window is released in the new position.
06/01/2009 10:15:27   Also see the -help entry for tuning parameters.
06/01/2009 10:15:27   You can press 3 Alt_L's (Left "Alt" key) in a row to 
06/01/2009 10:15:27   repaint the screen, also see the -fixscreen option for
06/01/2009 10:15:27   periodic repaints.
06/01/2009 10:15:27 
06/01/2009 10:15:27 XFIXES available on display, resetting cursor mode
06/01/2009 10:15:27   to: '-cursor most'.
06/01/2009 10:15:27   to disable this behavior use: '-cursor arrow'
06/01/2009 10:15:27   or '-noxfixes'.
06/01/2009 10:15:27 using XFIXES for cursor drawing.
06/01/2009 10:15:27 GrabServer control via XTEST.
06/01/2009 10:15:27 
06/01/2009 10:15:27 Scroll Detection: -scrollcopyrect mode is in effect to
06/01/2009 10:15:27   use RECORD extension to try to detect scrolling windows
06/01/2009 10:15:27   (induced by either user keystroke or mouse input).
06/01/2009 10:15:27   If this yields undesired behavior (poor response, painting
06/01/2009 10:15:27   errors, etc) it may be disabled via: '-noscr'
06/01/2009 10:15:27   Also see the -help entry for tuning parameters.
06/01/2009 10:15:27   You can press 3 Alt_L's (Left "Alt" key) in a row to 
06/01/2009 10:15:27   repaint the screen, also see the -fixscreen option for
06/01/2009 10:15:27   periodic repaints.
06/01/2009 10:15:27 
06/01/2009 10:15:27 XKEYBOARD: number of keysyms per keycode 6 is greater
06/01/2009 10:15:27   than 4 and 198 keysyms are mapped above 4.
06/01/2009 10:15:27   Automatically switching to -xkb mode.
06/01/2009 10:15:27   If this makes the key mapping worse you can
06/01/2009 10:15:27   disable it with the "-noxkb" option.
06/01/2009 10:15:27   Also, remember "-remap DEAD" for accenting characters.
06/01/2009 10:15:27 X FBPM extension not supported.
06/01/2009 10:15:27 X display is capable of DPMS.
06/01/2009 10:15:27 --------------------------------------------------------
06/01/2009 10:15:27 
06/01/2009 10:15:27 Default visual ID: 0x21
06/01/2009 10:15:28 Read initial data from X display into framebuffer.
06/01/2009 10:15:28 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/4608
06/01/2009 10:15:28 
06/01/2009 10:15:28 X display :0.0 is 32bpp depth=24 true color
06/01/2009 10:15:28 
06/01/2009 10:15:28 Listening for VNC connections on TCP port 5900
06/01/2009 10:15:28 
06/01/2009 10:15:28 Xinerama is present and active (e.g. multi-head).
06/01/2009 10:15:28 Xinerama: enabling -xwarppointer mode to try to correct
06/01/2009 10:15:28 Xinerama: mouse pointer motion. XTEST+XINERAMA bug.
06/01/2009 10:15:28 Xinerama: Use -noxwarppointer to force XTEST.
06/01/2009 10:15:28 fb read rate: 15 MB/sec
06/01/2009 10:15:28 screen setup finished.
06/01/2009 10:15:28 

The VNC desktop is:      TEST:0

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

more info: [http://www.karlrunge.com/x11vnc/#faq-client-caching](http://www.karlrunge.com/x11vnc/#faq-client-caching)

06/01/2009 10:15:31 Got connection from client 192.168.2.9
06/01/2009 10:15:31   other clients:
06/01/2009 10:15:31 Disabled X server key autorepeat.
06/01/2009 10:15:31   to force back on run: 'xset r on' (3 times)
06/01/2009 10:15:31 created xdamage object: 0x400028
06/01/2009 10:15:31 Client Protocol Version 3.8
06/01/2009 10:15:31 Protocol version sent 3.8, using 3.8
06/01/2009 10:15:31 rfbProcessClientSecurityType: executing handler for type 2
06/01/2009 10:15:32 Pixel format for client 192.168.2.9:
06/01/2009 10:15:32   32 bpp, depth 24, little endian
06/01/2009 10:15:32   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
06/01/2009 10:15:32 no translation needed
06/01/2009 10:15:32 rfbProcessClientNormalMessage: ignoring unsupported encoding type zlibhex
06/01/2009 10:15:32 Enabling X-style cursor updates for client 192.168.2.9
06/01/2009 10:15:32 Enabling full-color cursor updates for client 192.168.2.9
06/01/2009 10:15:32 Enabling cursor position updates for client 192.168.2.9
06/01/2009 10:15:32 Using image quality level 6 for client 192.168.2.9
06/01/2009 10:15:32 Enabling LastRect protocol extension for client 192.168.2.9
06/01/2009 10:15:32 Enabling NewFBSize protocol extension for client 192.168.2.9
06/01/2009 10:15:32 Using tight encoding for client 192.168.2.9
06/01/2009 10:15:34 client 1 network rate 68.8 KB/sec (2043.5 eff KB/sec)
06/01/2009 10:15:34 client 1 latency:  2.5 ms
06/01/2009 10:15:34 dt1: 0.0662, dt2: 1.8846 dt3: 0.0025 bytes: 134190
06/01/2009 10:15:34 link_rate: LR_BROADBAND - 2 ms, 68 KB/s
+++++++++++++++++++++
That's what I have.

---

### Post by irvin on 2009-01-06
Hi

As I have nothing better to do I made another test ;-)

Ubuntu 7.10 64-bit - with updates until today
openssh-server
x11vnc 0.8.2
Virtualbox 2.1.0

I disconnected mouse, keyboard, display and restarted.
With this I can connect via putty/vnc to the Ubuntu Host an start Virtualbox and VM's ! This does work !!!

What I also did is to install ATI Graphics Driver (as I have a Motherboard mit AMD 690G Chipset and integrated graphics). After I did this i couldn't connect via putty/vnc to both Ubuntu, 8.04 and 8.10 !! Putty worked but VNC Viewer was disconnected immediately.

Then I wanted to start 8.04 or 8.10 directly on the host with mouse, keyboard and display. Sometimes I could log in but never get my desktop, mostly i only get a black screen !!! No way to deinstall the ATI Drivers. For new tests I have to reinstall 8.04 or 8.10. That's what I did the last 8 hours :-(

---

### Post by krunge on 2009-01-06
I looked at your logs.  From what you have said, it really seems like your X server is crashing (you said GDM login prompt is back up and no previous apps running.)

Did the X server really crash and not log anything?  Or did you miss the log somehow?  Note, if GDM restarts you may need to look in Xorg.0.log.old (or if that gets overwritten do something tricky.)

Also, what happens if you take the keyboard, mouse, and monitor off one by one (or did you do that already?)

---

### Post by irvin on 2009-01-07
Hi

At first here's what I did when I installed x11vnc:

I put this line in this to files:
/etc/gdm/Init/Default
and
/etc/gdm/PreSession/Default

/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900 - xrandr

and changed in:
/etc/gdm/gdm.conf
from
#KillInitClients=true
to
KillInitClients=true

and in this file:
/etc/gdm/gdm.conf-custom

I did this in the deamon section:
KillInitClients=true

OK. I only disconnected the monitor (mouse and keyboard were connected) and tried again. It crashes again !

Yes, I have to login again and there are no other programs running. I looked at the file dates and time in the var/log directory and gave all with newer date/time. That's all I have.

I looked in the Xorg.0.log.old file but could's find a time where it happend. It happend about 12:06.

Here's a part of the file (edited):
+++++++++++++++++++++++
Xorg.0.log.old

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x65) [0x480f35]
1: /lib/libc.so.6 [0x7f66e9e12060]
2: /usr/X11R6/bin/X(VidModeGetFirstModeline+0x85) [0x485995]
3: /usr/X11R6/bin/X(VidModeGetNumOfModes+0x42) [0x485a32]
4: /usr/lib/xorg/modules/extensions//libextmod.so [0x7f66e9729031]
5: /usr/X11R6/bin/X(Dispatch+0x364) [0x44d6e4]
6: /usr/X11R6/bin/X(main+0x45d) [0x4336fd]
7: /lib/libc.so.6(__libc_start_main+0xe6) [0x7f66e9dfd466]
8: /usr/X11R6/bin/X [0x432ad9]
Saw signal 11.  Server aborting.
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) ImPS/2 Logitech Wheel Mouse: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) AIGLX: Suspending AIGLX clients for VT switch
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdfffd800 0xdfffd800
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): avivo_restore !
Enable CRTC 0 success
Unblank CRTC 0 success
+++++++++++++++++++++++

---

### Post by krunge on 2009-01-07
There's your X server crash, complete with a backtrace:

> **irvin said:**
> 

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x65) [0x480f35]
1: /lib/libc.so.6 [0x7f66e9e12060]
2: /usr/X11R6/bin/X(VidModeGetFirstModeline+0x85) [0x485995]
3: /usr/X11R6/bin/X(VidModeGetNumOfModes+0x42) [0x485a32]
4: /usr/lib/xorg/modules/extensions//libextmod.so [0x7f66e9729031]
5: /usr/X11R6/bin/X(Dispatch+0x364) [0x44d6e4]
6: /usr/X11R6/bin/X(main+0x45d) [0x4336fd]
7: /lib/libc.so.6(__libc_start_main+0xe6) [0x7f66e9dfd466]
8: /usr/X11R6/bin/X [0x432ad9]
Saw signal 11.  Server aborting.


You might want to google for some of the function names in there (plus other relavant terms.)

Since it is looking for a video mode that suggests to me the lack of monitor is the problem.  Does it work with only the monitor attached?  

Perhaps you can get it to work by hardwiring some (modest) video modes (e.g. "ModeLine" option in xorg.conf.)

I've never used Virtualbox so I don't know what it might be inducing.

I don't think you've provided anything that suggests x11vnc is the problem,  right?  So I think the X server crash could be repeated w/o any x11vnc (all you would have to do is script everything somehow.)

Even w/o core hardware (i.e. monitor) the X server shouldn't crash like that; you might want to report a bug once you narrow down the problem.

---

### Post by irvin on 2009-01-07
Hi

Thanx ! I google for some of this and found a few with x server crashes. Some says it's the nvidia driver (i have ATI), some say it's a intel video driver problem and have a patch and...
So I'm not really sure where the Problem is.

I just installed today on a complete different machine, it's all the same, it crashes. Both are ATI Video Card but very different ones. So I don't think tyhat ati, nvidia and intel made the same mistake ?

It's probably the X-Server.
xorg.conf is not used anymore in Ubuntu 8.10 and just part of in 8.04. I found others things like the new monitors.xml file, but as the new Ubuntu "likes" to automatically looks for the hardware and the EDID infos from the Monitors, it seems that's a big Problem.

I just read about people who have KVM Switches, and the have Problems too. I don't think that's the way Ubuntu should go.
Automatically find the hardware but did no one thought about KVM and Servers ?

No, I don't think x11vnc has anything do to with this. After thinking about it and see that a new x session is started ist could not be from x11.

Do you know how to edit the title ? I couldn't find anything.
I think there's no solution for me right now.

I tried to install nxserver today, after 10 Hours it worked, but I wanted to see native display (shadowing). Finally I got everything working, BUT, the Keyboard doesn't work, Only the Mouse. The maybe last step won't work, I'm getting crazy !!!

For all, I'd like to use x11vnc because this works now for a long time very well for me. Maybe I'm will go for Ubuntu 7.10 with this server.
Thanx

---

### Post by krunge on 2009-01-07
> **irvin said:**
> 
I tried to install nxserver today, after 10 Hours it worked, but I wanted to see native display (shadowing). Finally I got everything working, BUT, the Keyboard doesn't work, Only the Mouse. The maybe last step won't work, I'm getting crazy !!!


If NX is giving problems, how do things go if you use "vncserver" (e.g. realvnc or tightvnc server)?

Another similar option (a poor man's vncserver) is the 'x11vnc -create' option (it requires you install the Xvfb package):

[http://www.karlrunge.com/x11vnc/faq.html#faq-xvfb](http://www.karlrunge.com/x11vnc/faq.html#faq-xvfb)


Also, post your xorg.conf maybe there is something that can be tweaked.

Along that line, why not try the "vesa" driver in xorg.conf.  Since you are running headless it will be much faster for x11vnc than ati or radeon.

---

### Post by irvin on 2009-01-08
Hi

As mostly, it takes a long long time to have something running like you want. I was really satisfied with x11vnc because it did what I like to have. The only strange thing with x11vnx was, As I use it with 7.04 and x11vnx Version 0.8.2 that I couldn't use the numeric keys on the right side of the Keyboard. As I tried with 8.04 and 8.10 it worked sometimes and now it's not working anymore, why this ?

I thought about the VESA driver, but the xorg.conf is not in use anymore. And the you can't also fix things in the Monitors.xml file. I think I'm looking to install the Vesa Driver or ...
Thanx again

---

### Post by krunge on 2009-01-08
> **irvin said:**
> 
I thought about the VESA driver, but the xorg.conf is not in use anymore.

You've said this a few times, and I am confused by what you mean.

I have an ubuntu 8.10 install on a test machine in my basement and it still uses xorg.conf.  I.e. I make edits to xorg.conf and restart gdm and see my changes applied (e.g. I just changed the max res to 800x600, driver to "vesa", etc.)

Where is it documented that xorg.conf is now ignored?

---

### Post by irvin on 2009-01-08
Hi

I solved my Problem. It worked in 8.10 and 8.04 !
I installed a fresh 8.04 with all updates and uninstalled this video driver via Synaptic
(xserver-xorg-video-ati 1:6.8.0-1)
and made a reboot. Than I changed the xorg.conf.

In 8.10 my xorg.conf was empty ! In 8.04 I deleted everything and put this into it:
+++++++++++++++++++
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
	
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Standardgrafikkarte"
	Driver		"vesa"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"SAMSUNG"
	Option		"DPMS"
	HorizSync	30-61
	VertRefresh	60-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Standardgrafikkarte"
	Monitor		"SAMSUNG"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
+++++++++++++++++++
I took this from another Ubuntu which is running without KVM, it was Ubuntu 7.04 ! But it worked, As it was the same Motherboard I probably didn't have a Problem with this:
BusID		"PCI:1:5:0"
With another Board this could be a Problem ?

Than i unplugged KVM and made a reboot.
With this settings I can run 8.04 and 8.10 with opennssh-server and x11vnc and I can start Virtualbox VM's from the client without crashing x-server on the host machine!
It could be so easy ?

A few things I noticed. In both 8.04 and 8.10. The settings in xorg.conf, after restart the stay untouched BUT, I have different resolutions than in the xorg.conf file in my display manager. That's so strange.

And in 8.04 the numeric keys form my keyboard work now with x11vnc, in 8.10 they didn't !

---

