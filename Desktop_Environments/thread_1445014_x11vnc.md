---
title: "x11vnc"
date: 2010-04-02
forum: Desktop Environments
---

### Post by sandrocchio_0.1 on 2010-04-02
Hi there,
I am trying to set up a VNC remote connection from Ubuntu Hardy to Ubuntu Karmic.
I'm following the guide / tutorial on the Italian Ubuntu community https://help.ubuntu.com/community/VNC, so I basically established a local port forwarding

ssh -L 5900:localhost:5900 [EMAIL="myself@moon.local"]myself@moon.local[/EMAIL]

and next I call
x11vnc -safer -localhost -nopw -once -display :1


The last command goes fine only if an already X session is open with the same user. I need an analogue to vncserver that on system boot automatically starts X sessions for my users, otherwise at the first remote host reboot I'll be cut off. I would appreciate if someone could confirm that x11vnc is not able to start X sessions automatically as for instance VNC Server on RedHat does.

Second thing, quite strage, even if x11vnc doesn't seems to be appropriate to my needs, I wanted to move forward and see how it was. As soon as I tried to open the vnc session on localhost:5900 (port forward), the local network connection kept dropping on both machines. This is the log from the client

Apr  2 08:05:30 athokos NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr  2 08:05:30 athokos NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr  2 08:05:30 athokos NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr  2 08:05:30 athokos NetworkManager: <info>  Config: set interface ap_scan to 1 
Apr  2 08:05:30 athokos NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Apr  2 08:05:30 athokos nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Apr  2 08:05:33 athokos NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Apr  2 08:05:33 athokos NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Apr  2 08:05:43 athokos NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Apr  2 08:05:48 athokos NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Apr  2 08:05:48 athokos NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Apr  2 08:05:49 athokos NetworkManager: <info>  wlan0: link timed out. 



the x11vnc shell on the remote host while the connection was dropping

02/04/2010 08:00:19 --------------------------------------------------------
02/04/2010 08:00:19 
02/04/2010 08:00:19 Default visual ID: 0x21
02/04/2010 08:00:20 Read initial data from X display into framebuffer.
02/04/2010 08:00:20 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/5464
02/04/2010 08:00:20 WARNING: Width (1366) is not a multiple of 4. VncViewer has problems with that.
02/04/2010 08:00:20 
02/04/2010 08:00:20 X display :1.0 is 32bpp depth=24 true color
02/04/2010 08:00:20 
02/04/2010 08:00:20 Autoprobing TCP port 
02/04/2010 08:00:20 Autoprobing selected port 5900
02/04/2010 08:00:20 
02/04/2010 08:00:20 Xinerama is present and active (e.g. multi-head).
02/04/2010 08:00:20 Xinerama: enabling -xwarppointer mode to try to correct
02/04/2010 08:00:20 Xinerama: mouse pointer motion. XTEST+XINERAMA bug.
02/04/2010 08:00:20 Xinerama: Use -noxwarppointer to force XTEST.
02/04/2010 08:00:20 fb read rate: 17 MB/sec
02/04/2010 08:00:20 screen setup finished.
02/04/2010 08:00:20 

The VNC desktop is:      localhost:0
PORT=5900

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

more info: [http://www.karlrunge.com/x11vnc/#faq-client-caching](http://www.karlrunge.com/x11vnc/#faq-client-caching)

02/04/2010 08:01:36 Got connection from client 127.0.0.1
02/04/2010 08:01:36   other clients:
02/04/2010 08:01:36 check_access: client 127.0.0.1 matches host 127.0.0.1
02/04/2010 08:01:36 Disabled X server key autorepeat.
02/04/2010 08:01:36   to force back on run: 'xset r on' (3 times)
02/04/2010 08:01:36 created xdamage object: 0x40002f
02/04/2010 08:01:36 Client Protocol Version 3.8
02/04/2010 08:01:36 Protocol version sent 3.8, using 3.8
02/04/2010 08:01:36 rfbProcessClientSecurityType: executing handler for type 1
02/04/2010 08:01:36 rfbProcessClientSecurityType: returning securityResult for client rfb version >= 3.8
02/04/2010 08:01:37 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0xFFFFFEFE)
02/04/2010 08:01:37 Enabling NewFBSize protocol extension for client 127.0.0.1
02/04/2010 08:01:37 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0x574D5669)
02/04/2010 08:01:37 Enabling full-color cursor updates for client 127.0.0.1
02/04/2010 08:01:37 Enabling X-style cursor updates for client 127.0.0.1
02/04/2010 08:01:37 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0xFFFFFEFF)
02/04/2010 08:01:37 Using tight encoding for client 127.0.0.1


Thanks for any help

---

### Post by krunge on 2010-04-02
> 
so I basically established a local port forwarding

ssh -L 5900:localhost:5900 [email]myself@moon.local[/email]

and next I call
x11vnc -safer -localhost -nopw -once -display :1

The last command goes fine only if an already X session is open with the same user. 

For reference, how do you get an X server on DISPLAY :1 instead of (or in addition to) DISPLAY :0 ?
> 
I need an analogue to vncserver that on system boot automatically starts X sessions for my users, otherwise at the first remote host reboot I'll be cut off. I would appreciate if someone could confirm that x11vnc is not able to start X sessions automatically as for instance VNC Server on RedHat does.

x11vnc can start Virtual (RAM-only) X server sessions on demand.  It starts Xvfb, so you need to install the **xvfb** package.

It can be made available at boot-time.  I usually use inetd for that. It is described here:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-userlogin](http://www.karlrunge.com/x11vnc/faq.html#faq-userlogin)[/INDENT]
The x11vnc '-svc' option is an alias for 1) enable SSL encryption, 2) allow user to login via Unix username and passwd, 3) try to find the user's existing X session, 4) if not found, create a new (Xvfb) X session.

It can be tricky to set up though, if you try it I can try to help you if you have any difficulties.

---

### Post by sandrocchio_0.1 on 2010-04-07
> **krunge said:**
> For reference, how do you get an X server on DISPLAY :1 instead of (or in addition to) DISPLAY :0 ?

x11vnc can start Virtual (RAM-only) X server sessions on demand.  It starts Xvfb, so you need to install the **xvfb** package.

It can be made available at boot-time.  I usually use inetd for that. It is described here:[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-userlogin](http://www.karlrunge.com/x11vnc/faq.html#faq-userlogin)[/INDENT]The x11vnc '-svc' option is an alias for 1) enable SSL encryption, 2) allow user to login via Unix username and passwd, 3) try to find the user's existing X session, 4) if not found, create a new (Xvfb) X session.

It can be tricky to set up though, if you try it I can try to help you if you have any difficulties.

Thanks for your help, I'll give a try later on since I already spent some time on it and this is not on the top of my project list.
Regarding your question, I guess :0,:1,etc. are X sessions, so since I already locally logged in the next available session was :1 However I suspect you can call any session ID you like unless they're already used.

Thanks again for now.

---

### Post by krunge on 2010-04-07
> **sandrocchio_0.1 said:**
> 
Regarding your question, I guess :0,:1,etc. are X sessions, so since I already locally logged in the next available session was :1 However I suspect you can call any session ID you like unless they're already used.

Ah, so multiple X session logins on the same physical console?  I.e. the type you can switch between with Ctrl-Alt-F7, Ctrl-Alt-F8, etc.

BTW, if you are using x11vnc to view one of those, it needs to be the visible one on the console to be able to see screen updates:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-linuxvc](http://www.karlrunge.com/x11vnc/faq.html#faq-linuxvc)[/INDENT]

---

