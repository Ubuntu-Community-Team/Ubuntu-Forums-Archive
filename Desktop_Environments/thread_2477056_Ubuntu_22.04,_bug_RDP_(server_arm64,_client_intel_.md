---
title: "Ubuntu 22.04, bug RDP (server arm64, client intel x86)"
date: 2022-07-13
forum: Desktop Environments
---

### Post by petitbouchon on 2022-07-13
hello,  
ubuntu 22.04 arm64 on rapberry pi with remote desktop rdp server. 
ubuntu 22.04 x86 on my main workstation as a client with reminna. 
1 - at each boot the server's RDP password changes (by itself). 
2 - On the client, the image of the remote desktop is scrambled. If I touch the image the RDP connection restarts.

[IMG][[IMG]https://zupimages.net/up/22/28/1g41.png[/IMG]]("https://zupimages.net/viewer.php?id=22/28/1g41.png")[/IMG]

---

### Post by TheFu on 2022-07-13
Do VNC or NX protocols work better?

I've not used RDP in about a decade.  Also, most remote desktops don't like Gnome, so install and use a lighter DE, if you need a DE at all.

Are the screen resolutions set correctly on each side of the connection?  I could see where a r-pi v4 might expect a 4k display, but the desktop might be limited to a 1920x1200p resolution (or lower).  I think the requested display resolution can be provided on the command line with all the remote desktop tools.

Just some ideas.

---

### Post by petitbouchon on 2022-07-14
Hello
 With a good tutorial I managed the configuration. so install xrdp (and not vino) enable and start. 
It's OK. except that I have a french keyboard (AZERTY) and I find myself on the remote screen with a keyboard QWERTY

---

### Post by petitbouchon on 2022-07-14
Well!
 it doesn't work anymore. 
Below syslog message on the RDP client workstation.
> 
Jul 14 14:56:57 herve-W54-55SU1-SUW org.remmina.Remmina.desktop[1826]: [14:56:57:955] [1826:6480] [ERROR][com.freerdp.common.settings] - [freerdp_settings_get_bool] Invalid key index 131
Jul 14 14:56:57 herve-W54-55SU1-SUW org.remmina.Remmina.desktop[1826]: [14:56:57:955] [1826:6480] [ERROR][com.freerdp.common.settings] - [freerdp_settings_get_bool] Invalid key index 0
Jul 14 14:57:17 herve-W54-55SU1-SUW org.remmina.Remmina.desktop[1826]: [14:57:17:682] [1826:6480] [ERROR][com.freerdp.core] - rdp_set_error_info:freerdp_set_last_error_ex ERRINFO_LOGOFF_BY_USER [0x0001000C]



---

### Post by TheFu on 2022-07-14
> **petitbouchon said:**
> Hello
 With a good tutorial I managed the configuration. so install xrdp (and not vino) enable and start. 
It's OK. except that I have a french keyboard (AZERTY) and I find myself on the remote screen with a keyboard QWERTY

You can change the keyboard, if needed. Since I use ssh, the keyboard is from the client. With a remote desktop, I'd expect that using the DEs keyboard selection tool should work on a per-userid basis.

---

### Post by petitbouchon on 2022-07-15
Hello
After the first successful try, I changed the sd card on the raspberrypi rdp server for a new card configured with xrdp ubuntu 22.04 but with a default xorg configuration (without screen), the connection is established but without display ( black or blue screen). Since , raspberrypi with a screen, the connection closes as soon as login/password is validated regardless of the SD card put in the RPi.
Below syslog message on server
> 
Jul 15 09:10:23 pi-desktop xrdp[920]: [INFO ] Socket 12: AF_INET6 connection received from ::ffff:192.168.1.192 port 60372
Jul 15 09:10:23 pi-desktop xrdp[2298]: [INFO ] Using default X.509 certificate: /etc/xrdp/cert.pem
Jul 15 09:10:23 pi-desktop xrdp[2298]: [INFO ] Using default X.509 key file: /etc/xrdp/key.pem
Jul 15 09:10:23 pi-desktop xrdp[2298]: [ERROR] Cannot read private key file /etc/xrdp/key.pem: Permission denied
Jul 15 09:10:23 pi-desktop xrdp[2298]: [INFO ] Connected client computer name: herve-W54-55SU1
Jul 15 09:10:23 pi-desktop xrdp[2298]: [WARN ] Received [MS-RDPBCGR] TS_UD_HEADER type 0xc006 is unknown (ignored)
Jul 15 09:10:23 pi-desktop xrdp[2298]: [WARN ] Received [MS-RDPBCGR] TS_UD_HEADER type 0xc00a is unknown (ignored)
Jul 15 09:10:24 pi-desktop xrdp[2298]: [INFO ] xrdp_load_keyboard_layout: Keyboard information sent by the RDP client, keyboard_type:[0x04], keyboard_subtype:[0x00], keylayout:[0x00000409]
Jul 15 09:10:24 pi-desktop xrdp[2298]: [INFO ] xrdp_load_keyboard_layout: model [] variant [] layout [us] options []
Jul 15 09:10:24 pi-desktop xrdp[2298]: [INFO ] Non-TLS connection established from ::ffff:192.168.1.192 port 60372: encrypted with standard RDP security
Jul 15 09:10:24 pi-desktop xrdp[2298]: [INFO ] xrdp_caps_process_pointer: client supports new(color) cursor
Jul 15 09:10:24 pi-desktop xrdp[2298]: [INFO ] xrdp_process_offscreen_bmpcache: support level 1 cache size 7864320 MB cache entries 2000
Jul 15 09:10:24 pi-desktop xrdp[2298]: [INFO ] xrdp_caps_process_codecs: RemoteFX, codec id 3, properties len 49
Jul 15 09:10:24 pi-desktop xrdp[2298]: [WARN ] Client Capability: not enough orders supported by client, client wants off screen bitmap but offscreen bitmaps disabled
Jul 15 09:10:25 pi-desktop xrdp[2298]: [INFO ] Loading keymap file /etc/xrdp/km-00000409.ini
Jul 15 09:10:25 pi-desktop xrdp[2298]: [WARN ] local keymap file for 0x00000409 found and doesn't match built in keymap, using local keymap file
Jul 15 09:10:39 pi-desktop xrdp[2298]: [INFO ] connecting to sesman ip 127.0.0.1 port 3350
Jul 15 09:10:39 pi-desktop xrdp-sesman[887]: [INFO ] Socket 8: AF_INET6 connection received from ::1 port 51674
Jul 15 09:10:39 pi-desktop xrdp[2298]: [INFO ] xrdp_wm_log_msg: sesman connect ok
Jul 15 09:10:39 pi-desktop xrdp[2298]: [INFO ] sesman connect ok
Jul 15 09:10:39 pi-desktop xrdp[2298]: [INFO ] sending login info to session manager, please wait...
Jul 15 09:10:39 pi-desktop xrdp-sesman[887]: [INFO ] Terminal Server Users group is disabled, allowing authentication
Jul 15 09:10:39 pi-desktop xrdp-sesman[887]: [INFO ] ++ created session (access granted): username pi, ip ::ffff:192.168.1.192:60372 - socket: 12
Jul 15 09:10:39 pi-desktop xrdp-sesman[887]: [INFO ] starting Xorg session...
Jul 15 09:10:39 pi-desktop xrdp-sesman[887]: [ERROR] g_tcp_bind(9, 6010) failed bind IPv6 (errno=98) and IPv4 (errno=22).
Jul 15 09:10:39 pi-desktop xrdp-sesman[887]: [INFO ] Found X server running at 6010
Jul 15 09:10:39 pi-desktop xrdp-sesman[887]: [INFO ] Starting session: session_pid 2302, display :11.0, width 592, height 440, bpp 24, client ip ::ffff:192.168.1.192:60372 - socket: 12, user name pi
Jul 15 09:10:39 pi-desktop xrdp-sesman[2302]: [INFO ] [session start] (display 11): calling auth_start_session from pid 2302
Jul 15 09:10:39 pi-desktop xrdp-sesman[887]: [ERROR] sesman_data_in: scp_process_msg failed
Jul 15 09:10:39 pi-desktop xrdp[2298]: [INFO ] xrdp_wm_log_msg: login successful for display 11
Jul 15 09:10:39 pi-desktop xrdp[2298]: [INFO ] login successful for display 11
Jul 15 09:10:39 pi-desktop xrdp-sesman[887]: [ERROR] sesman_main_loop: trans_check_wait_objs failed, removing trans
Jul 15 09:10:39 pi-desktop xrdp[2298]: [INFO ] loaded module 'libxup.so' ok, interface size 10296, version 4
Jul 15 09:10:39 pi-desktop xrdp[2298]: [INFO ] started connecting
Jul 15 09:10:39 pi-desktop xrdp[2298]: [INFO ] lib_mod_connect: connecting via UNIX socket
Jul 15 09:10:39 pi-desktop systemd[1]: Started Session c3 of User pi.
Jul 15 09:10:39 pi-desktop xrdp-sesman[2304]: [INFO ] Starting X server on display 11: /usr/lib/xorg/Xorg :11 -auth .Xauthority -config xrdp/xorg.conf -noreset -nolisten tcp -logfile .xorgxrdp.%s.log  
Jul 15 09:10:39 pi-desktop xrdp-sesman[2303]: [INFO ] Found X server running at /tmp/.X11-unix/X11
Jul 15 09:10:39 pi-desktop xrdp-sesman[2302]: [INFO ] Found X server running at /tmp/.X11-unix/X11
Jul 15 09:10:39 pi-desktop xrdp-sesman[2303]: [INFO ] Found X server running at /tmp/.X11-unix/X11
Jul 15 09:10:39 pi-desktop xrdp-sesman[2302]: [INFO ] Session started successfully for user pi on display 11
Jul 15 09:10:39 pi-desktop xrdp-sesman[2308]: [INFO ] Starting the xrdp channel server for display 11
Jul 15 09:10:39 pi-desktop xrdp-sesman[2302]: [INFO ] Session in progress on display 11, waiting until the window manager (pid 2303) exits to end the session
Jul 15 09:10:39 pi-desktop xrdp-sesman[2303]: [INFO ] Starting the default window manager on display 11: /etc/xrdp/startwm.sh
Jul 15 09:10:39 pi-desktop xrdp[2298]: [INFO ] lib_mod_log_peer: xrdp_pid=2298 connected to X11rdp_pid=2304 X11rdp_uid=1000 X11rdp_gid=1000 client_ip=::ffff:192.168.1.192 client_port=60372
Jul 15 09:10:39 pi-desktop xrdp[2298]: [INFO ] connected ok
Jul 15 09:10:39 pi-desktop xrdp-chansrv[2308]: [INFO ] Socket 12: AF_UNIX connection received
Jul 15 09:10:40 pi-desktop xrdp-chansrv[2308]: [INFO ] sound_process_training: round trip time 102
Jul 15 09:10:41 pi-desktop gnome-session[2406]: gnome-session-check-accelerated: no X11 display found
Jul 15 09:10:41 pi-desktop gnome-session[2426]: gnome-session-check-accelerated: no X11 display found
Jul 15 09:10:41 pi-desktop gnome-session[2303]: gnome-session-binary[2303]: WARNING: software acceleration check failed: Le processus fils s&#8217;est terminé avec le code 1
Jul 15 09:10:41 pi-desktop gnome-session-binary[2303]: WARNING: software acceleration check failed: Le processus fils s&#8217;est terminé avec le code 1
Jul 15 09:10:41 pi-desktop gnome-session-f[2436]: Cannot open display: 
Jul 15 09:10:41 pi-desktop xrdp-sesman[2302]: [WARN ] Window manager (pid 2303, display 11) exited with non-zero exit code 255 and signal 15. This could indicate a window manager config problem
Jul 15 09:10:41 pi-desktop xrdp-sesman[2302]: [WARN ] Window manager (pid 2303, display 11) exited quickly (2 secs). This could indicate a window manager config problem
Jul 15 09:10:41 pi-desktop xrdp-sesman[2302]: [INFO ] Calling auth_stop_session and auth_end from pid 2302
Jul 15 09:10:41 pi-desktop xrdp-sesman[2302]: [INFO ] Terminating X server (pid 2304) on display 11
Jul 15 09:10:41 pi-desktop xrdp-sesman[2302]: [INFO ] Terminating the xrdp channel server (pid 2308) on display 11
Jul 15 09:10:41 pi-desktop systemd[1]: home-pi-thinclient_drives.mount: Deactivated successfully.
Jul 15 09:10:41 pi-desktop xrdp-sesman[2302]: [INFO ] X server on display 11 (pid 2304) returned exit code 0 and signal number 0
Jul 15 09:10:41 pi-desktop xrdp-sesman[2302]: [INFO ] xrdp channel server for display 11 (pid 2308) exit code 0 and signal number 0
Jul 15 09:10:41 pi-desktop xrdp-sesman[2302]: [INFO ] cleanup_sockets:
Jul 15 09:10:41 pi-desktop xrdp-sesman[887]: [INFO ] ++ terminated session:  username pi, display :11.0, session_pid 2302, ip ::ffff:192.168.1.192:60372 - socket: 12
Jul 15 09:10:50 pi-desktop systemd[1]: session-c3.scope: Deactivated successfully.
Jul 15 09:10:50 pi-desktop systemd[1]: session-c3.scope: Consumed 3.611s CPU time.


---

### Post by ActionParsnip on 2022-07-15
What are you doing on the system that needs the full desktop session? There may be a sleeker solution to what you want to achieve

---

### Post by petitbouchon on 2022-07-16
Hello 
Still on my RPi without screen looking to setup an ubuntu 22.04 install with xrdp to connect. 
I figured out that to establish the connection the server needed to not be running a local session. So autologin= false 
The session on the client opens after entering the login and password (still the QWERTY keyboard problem on this window). 
New problem my display is in 4/3 592x440 50.00Hz and no modification possible in parameters/screens. A priori the configuration is in /etc/X11/xrdp/xorg.conf 
Below the file in place.

> pi@pi-desktop:~$ cat /etc/X11/xrdp/xorg.conf

Section "ServerLayout"
    Identifier "X11 Server"
    Screen "Screen (xrdpdev)"
    InputDevice "xrdpMouse" "CorePointer"
    InputDevice "xrdpKeyboard" "CoreKeyboard"
EndSection

Section "ServerFlags"
    # This line prevents "ServerLayout" sections in xorg.conf.d files
    # overriding the "X11 Server" layout (xrdp #1784)
    Option "DefaultServerLayout" "X11 Server"
    Option "DontVTSwitch" "on"
    Option "AutoAddDevices" "off"
EndSection

Section "Module"
    Load "dbe"
    Load "ddc"
    Load "extmod"
    Load "glx"
    Load "int10"
    Load "record"
    Load "vbe"
    Load "glamoregl"
    Load "xorgxrdp"
    Load "fb"
EndSection

Section "InputDevice"
    Identifier "xrdpKeyboard"
    Driver "xrdpkeyb"
EndSection

Section "InputDevice"
    Identifier "xrdpMouse"
    Driver "xrdpmouse"
EndSection

Section "Monitor"
    Identifier "Monitor"
    Option "DPMS"
    HorizSync 30-80
    VertRefresh 60-75
    ModeLine "1920x1080" 138.500 1920 1968 2000 2080 1080 1083 1088 1111 +hsync -vsync
    ModeLine "1280x720" 74.25 1280 1720 1760 1980 720 725 730 750 +HSync +VSync
    Modeline "1368x768" 72.25 1368 1416 1448 1528 768 771 781 790 +hsync -vsync
    Modeline "1600x900" 119.00 1600 1696 1864 2128 900 901 904 932 -hsync +vsync
EndSection

Section "Device"
    Identifier "Video Card (xrdpdev)"
    Driver "xrdpdev"
    Option "DRMDevice" "/dev/dri/renderD128"
    Option "DRI3" "1"
EndSection

Section "Screen"
    Identifier "Screen (xrdpdev)"
    Device "Video Card (xrdpdev)"
    Monitor "Monitor"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "640x480" "800x600" "1024x768" "1280x720" "1280x1024" "1600x900" "1920x1080"
    EndSubSection
EndSection


---

### Post by TheFu on 2022-07-16
x2go doesn't have these issues.  Just sayin'.
It uses ssh for authentication, so it is much more secure and convenient.
It uses better compression and allows control based on network performance. I've used it over an ISDN from a different continent.
x2go is extremely stable. I used it all day, every day for a few years to remote into my desktop and work.
x2go allows multiple sessions and doesn't care about what the local machine is doing. The same account can be used on the local screen as over a remote connection.  New connections can either reconnect to the same x2go session or create a new one. If you get everything setup on the desktop and running just the way you like it, a reconnect gets you back to that same setup.

x2go doesn't work with DEs that demand direct GPU access - so KDE and Gnome3+ don't work, but all other DEs and WMs do work. XFCE, Mate, Cinnamon, LXQt, fvwm, openbox, twm, mwm, whatever.

I understand if you are stubborn and want to use crappy solutions like RDP, but if you just want things that work, use x2go.  It is like comparing night and day. Performance feels 2-3x faster than any VNC or RDP I've seen.  Setup ssh with ssh-keys for the most convenience and security.

But I understand if you don't want to use something that works too. Good luck.

---

