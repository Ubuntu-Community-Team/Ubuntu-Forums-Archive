---
title: "google-chrome fails to display when launched under xfce on headless server"
date: 2018-09-03
forum: Desktop Environments
---

### Post by lau-5-jgbrown on 2018-09-03
[COLOR=#242729][FONT=Arial]I am having a problem launching Google Chrome 68.0.3440.106 on Ubuntu 18.04, running on a headless server via a TightVNC remote connection and xfce.

The odd part is that everything ran great until I moved the server to the upstairs office. Chrome displayed after it was installed. The server is running and connecting just fine from up there; I am streaming a movie via Plex as I write this.

But once I installed the server upstairs and restarted it, Chrome refuses to display on the VNC connection. Oddly, Firefox launches and displays just fine.

The command **google-chrome --version** runs without error in the terminal on the server. Here is the output from running google-chrome in a terminal on the server:
```
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
Xlib:  extension "XInputExtension" missing on display ":1.0".
[3137:3137:0903/123257.280567:ERROR:gl_surface_glx.cc(424)] glxQueryVersion failed
[3137:3137:0903/123257.280600:ERROR:gl_initializer_x11.cc(157)] GLSurfaceGLX::InitializeOneOff failed.
[3137:3137:0903/123257.282614:ERROR:viz_main_impl.cc(201)] Exiting GPU process due to errors during initialization
[3098:3113:0903/123257.283916:ERROR:service_manager_context.cc(250)] Attempting to run unsupported native service: /opt/google/chrome/content_gpu.service
Xlib:  extension "XInputExtension" missing on display ":1.0".

```
**Contents of ~/.vnc/xstartup :**
```
#!/bin/sh
def
export XKL_XMODMAP_DISABLE=1
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS

xrdb $HOME/.Xresources
xsetroot -solid grey

startxfce4 &

```
**Contents of vncserver service file /etc/systemd/system/vncserver@.service :**
```
[Unit]
Description=Start TightVNC server at startup
After=syslog.target network.target


[Service]
Type=forking
User=jgb
PAMName=login
PIDFile=/home/jgb/.vnc/%H:%i.pid
ExecStartPre=-/usr/bin/vncserver -kill :%i > /dev/null 2>&1
ExecStart=/usr/bin/vncserver -depth 24 -geometry 1280x720 :%i
ExecStop=/usr/bin/vncserver -kill :%i


[Install]
WantedBy=multi-user.target

```
Please advise: What have I overlooked?

Thanks...

JGB


[/FONT][/COLOR]

---

