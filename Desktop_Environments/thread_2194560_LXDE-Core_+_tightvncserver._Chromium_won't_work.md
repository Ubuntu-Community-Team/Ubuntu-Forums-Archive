---
title: "LXDE-Core + tightvncserver. Chromium won't work"
date: 2013-12-19
forum: Desktop Environments
---

### Post by genivasla on 2013-12-19
On a clean ubuntu VPS, I installed ```
apt-get install xorg lxde-core tightvncserver
``` with the following xstartup settings:

```
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession
lxterminal &
/usr/bin/lxsession -s LXDE &
```

I'm able to successfully VNC to the LXDE desktop. I then install chromium with: ```
sudo apt-get install chromium-browser
```

When I try to start chromium, the program launches and immediately crashes. When I try to run from the command line, I get the following message:

```
Xlib extension “RANDR” missing on display ":1"
```

For the life of me I can't figure out how to resolve this. I'm a newbie to all of this, and uncertain if this is an issue with LXDE or Tightvnc.

Any tips on what could be causing this? Let me know if there's any other information I can share.

---

### Post by steeldriver on 2013-12-19
I think it means that your tightvncserver does not support the Xlib RANDR extension - however this usually isn't fatal, I get the same message starting firefox in an LXDE session over tightvnc, but it runs just fine. *If* that's what's causing chromium to crash (and I have doubts about that) then arguably it's chromium's issue for not handling it more gracefully. I *think* that the RANDR extension should only be required for stuff like dynamic display resiszing / rotation.

If you still believe the missing RANDR support is the issue, you could try vnc4server instead of tightvncserver

---

### Post by genivasla on 2013-12-19
Thanks for the help. Any ideas on what else it could be? I literally only installed lxde-core and tightvnc. The only other setting that was made besides what was previously mentioned was the following to force tightvnc to start at boot...

```
vi /etc/init.d/tightvncserver
```

```
#!/bin/sh -e### BEGIN INIT INFO
# Provides:          vncserver
# Required-Start:    networking
# Default-Start:     S
# Default-Stop:      0 6
### END INIT INFO


PATH="$PATH:/usr/X11R6/bin/"


# The Username:Group that will run VNC
export USER="user1"
#${RUNAS}


# The display that VNC will use
DISPLAY="1"


# Color depth (between 8 and 32)
DEPTH="16"


# The Desktop geometry to use.
#GEOMETRY="<WIDTH>x<HEIGHT>"
#GEOMETRY="800x600"
GEOMETRY="1024x768"
#GEOMETRY="1280x1024"


# The name that the VNC Desktop will have.
NAME="dekstop1"


OPTIONS="-name ${NAME} -depth ${DEPTH} -geometry ${GEOMETRY} :${DISPLAY}"


. /lib/lsb/init-functions


case "$1" in
start)
log_action_begin_msg "Starting vncserver for user '${USER}' on localhost:${DISPLAY}"
su ${USER} -c "/usr/bin/vncserver ${OPTIONS}"
;;


stop)
log_action_begin_msg "Stoping vncserver for user '${USER}' on localhost:${DISPLAY}"
su ${USER} -c "/usr/bin/vncserver -kill :${DISPLAY}"
;;


restart)
$0 stop
$0 start
;;
esac


exit 0

```


```
sudo chmod +x /etc/init.d/tightvncserversudo update-rc.d tightvncserver defaults

```

---

### Post by steeldriver on 2013-12-19
Are there multiple users / X sessions / displays running? does it work if you only have a single active session / display?

---

### Post by genivasla on 2013-12-19
Just the one session and display running as far as I can tell. Firefox works just fine, but unfortunately need Chromium for this project.

---

### Post by steeldriver on 2013-12-19
Well I just tested it on my 12.04.03 laptop and chromium works for me on an lxsession via tightvnc

Maybe try starting chromium-browser with the  --temp-profile switch in case it's a profile corruption issue? if that fails, there's a -g or --debug option

---

### Post by genivasla on 2013-12-19
Thanks for testing that out for me! I'll give that a shot and report back...

---

### Post by genivasla on 2013-12-19
Unfortunately that didn't work. I tried running with xrdp vnc and same issue, so must be something other than the vlc.

---

### Post by genivasla on 2013-12-19
Installed lxde-core on a brand new vps and still having the same issue. I wonder if it has something to do with color depth or something simple I'm overlooking.

---

### Post by steeldriver on 2013-12-19
is there anything in ~/.xsession-errors (apart from the Xlib RANDR extension messages)?

---

### Post by genivasla on 2013-12-19
It's long... which is surprising consider this is a new VPS that only had chromium-browser installed and only ran a couple times.

```
Xsession: X session started for user1 at Thu Dec 19 13:05:21 EST 2013X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
localuser:user1 being added to access control list
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
Error org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to find session for cookie
Usage: dbus-send [--help] [--system | --session | --address=ADDRESS] [--dest=NAME] [--type=TYPE] [--print-reply=(literal)] [--reply-timeout=MSEC] <destination object path> <message name> [contents ...]
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".
Obt-Message: XKB extension is not present on the server or too old
Obt-Message: Xinerama extension is not present on the server
Obt-Message: XRandR extension is not present on the server


(polkit-gnome-authentication-agent-1:1093): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed


(polkit-gnome-authentication-agent-1:1093): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Openbox-Message: Requested key "Print" does not exist on the display
Openbox-Message: Requested key "Print" does not exist on the display
Openbox-Message: Requested key "XF86AudioRaiseVolume" does not exist on the display
Openbox-Message: Requested key "XF86AudioLowerVolume" does not exist on the display
Openbox-Message: Requested key "XF86AudioMute" does not exist on the display
Openbox-Message: Requested key "XF86WWW" does not exist on the display
Openbox-Message: Requested key "XF86Calculator" does not exist on the display
Openbox-Message: Requested key "XF86MyComputer" does not exist on the display
Openbox-Message: Requested key "XF86Terminal" does not exist on the display
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".
lxsession: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1"^M
      after 3968 requests (3709 known processed) with 0 events remaining.^M
lxpanel: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
Xsession: X session started for user1 at Thu Dec 19 13:09:57 EST 2013
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
localuser:user1 being added to access control list
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
Error org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to find session for cookie
Usage: dbus-send [--help] [--system | --session | --address=ADDRESS] [--dest=NAME] [--type=TYPE] [--print-reply=(literal)] [--reply-timeout=MSEC] <destination object path> <message name> [contents ...]
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".
Obt-Message: XKB extension is not present on the server or too old
Obt-Message: Xinerama extension is not present on the server
Obt-Message: XRandR extension is not present on the server


(polkit-gnome-authentication-agent-1:1082): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed


(polkit-gnome-authentication-agent-1:1082): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Openbox-Message: Requested key "Print" does not exist on the display
Openbox-Message: Requested key "Print" does not exist on the display
Openbox-Message: Requested key "XF86AudioRaiseVolume" does not exist on the display
Openbox-Message: Requested key "XF86AudioLowerVolume" does not exist on the display
Openbox-Message: Requested key "XF86AudioMute" does not exist on the display
Openbox-Message: Requested key "XF86WWW" does not exist on the display
Openbox-Message: Requested key "XF86Calculator" does not exist on the display
Openbox-Message: Requested key "XF86MyComputer" does not exist on the display
Openbox-Message: Requested key "XF86Terminal" does not exist on the display
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".


(obconf:1274): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
ObRender-Message: Unable to parse color '#0000000'


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed
ObRender-Message: Unable to parse color '#e3ca9c '


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed
ObRender-Message: Unable to parse color '#7eee8cf'


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed
ObRender-Message: Unable to parse color '#7eee8cf'
ObRender-Message: Unable to parse color ''
ObRender-Message: Unable to parse color '#3e71aac'


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed
ObRender-Message: Unable to parse color '#0000000'


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_fill: assertion `GDK_IS_PIXBUF (pixbuf)' failed


(obconf:1274): GdkPixbuf-CRITICAL **: gdk_pixbuf_copy_area: assertion `src_pixbuf != NULL' failed
Openbox-Message: Requested key "Print" does not exist on the display
Openbox-Message: Requested key "Print" does not exist on the display
Openbox-Message: Requested key "XF86AudioRaiseVolume" does not exist on the display
Openbox-Message: Requested key "XF86AudioLowerVolume" does not exist on the display
Openbox-Message: Requested key "XF86AudioMute" does not exist on the display
Openbox-Message: Requested key "XF86WWW" does not exist on the display
Openbox-Message: Requested key "XF86Calculator" does not exist on the display
Openbox-Message: Requested key "XF86MyComputer" does not exist on the display
Openbox-Message: Requested key "XF86Terminal" does not exist on the display
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".


** (lxsession-logout:1649): WARNING **: dbus-interface.c:94: DBUS: The name org.freedesktop.UPower was not provided by any .service files


** (lxsession-logout:1649): WARNING **: dbus-interface.c:94: DBUS: The name org.freedesktop.UPower was not provided by any .service files


** (lxsession-logout:1649): WARNING **: dbus-interface.c:94: DBUS: The name org.freedesktop.Hal was not provided by any .service files


** (lxsession-logout:1649): WARNING **: dbus-interface.c:94: DBUS: The name org.freedesktop.Hal was not provided by any .service files


** (lxsession-logout:1649): WARNING **: dbus-interface.c:94: DBUS: The name org.freedesktop.Hal was not provided by any .service files


** (lxsession-logout:1649): WARNING **: dbus-interface.c:94: DBUS: The name org.freedesktop.Hal was not provided by any .service files
Xlib:  extension "RANDR" missing on display ":1".


** (lxsession-logout:1668): WARNING **: dbus-interface.c:94: DBUS: The name org.freedesktop.UPower was not provided by any .service files


** (lxsession-logout:1668): WARNING **: dbus-interface.c:94: DBUS: The name org.freedesktop.UPower was not provided by any .service files


** (lxsession-logout:1668): WARNING **: dbus-interface.c:94: DBUS: The name org.freedesktop.Hal was not provided by any .service files


** (lxsession-logout:1668): WARNING **: dbus-interface.c:94: DBUS: The name org.freedesktop.Hal was not provided by any .service files


** (lxsession-logout:1668): WARNING **: dbus-interface.c:94: DBUS: The name org.freedesktop.Hal was not provided by any .service files


** (lxsession-logout:1668): WARNING **: dbus-interface.c:94: DBUS: The name org.freedesktop.Hal was not provided by any .service files


** (lxsession-logout:1668): WARNING **: dbus-interface.c:94: DBUS: The name org.freedesktop.Hal was not provided by any .service files
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".
Xlib:  extension "RANDR" missing on display ":1".


(pcmanfm:1081): Gtk-WARNING **: Radio group does not contain an action with value '0'
                                                                                                       
```

---

### Post by genivasla on 2013-12-19
I now installed lubuntu-core on a fresh VPS and having the same issue. The error message on lubuntu is:

```
Xlib:  extension "RANDR" missing on display ":1".[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "pixmap",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "pixmap",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "pixmap",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "pixmap",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "pixmap",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "clearlooks",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "pixmap",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "pixmap",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "clearlooks",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "clearlooks",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "pixmap",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "pixmap",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "pixmap",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "pixmap",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "pixmap",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "pixmap",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "pixmap",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "pixmap",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "pixmap",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "pixmap",
[26400:26400:1219/143456:ERROR:browser_main_loop.cc(208)] GTK theme error: Unable to locate theme engine in module_path: "clearlooks",
Illegal Instruction (core dumped)
```

---

### Post by steeldriver on 2013-12-19
Sorry I`m out of ideas - fwiw I just installed the following on a previously bare 12.04 server (i.e. command line only, no additional X components apart from whatever dependencies these packages bring in) 

```

$ dpkg -l chromium-browser tightvncserver lxde-core
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                      Version                                   Description
+++-=========================================-=========================================-==================================================================================================
ii  chromium-browser                          31.0.1650.63-0ubuntu0.12.04.1~20131204.1  Chromium browser
ii  lxde-core                                 0.5.0-4ubuntu3                            Meta-package for the Lightweight X11 Desktop Environment Core
ii  tightvncserver                            1.3.9-6.2ubuntu2                          virtual network computing server software

```

and again, it worked fine (apart from the Xlib RANDR extension warning).

---

### Post by genivasla on 2013-12-19
Yeah, something very strange going on here. I appreciate all the help and testing that out on your end.

---

### Post by genivasla on 2013-12-19
On one of the crashes, chromium produced an error report. The one item I noticed was can't open profile /home/user1/.config/chromium/Default/Preferences.
I added a Preferences folder and tried to relaunch and received the same error. The Preference folder was renamed to Preferences.bad.

I created new VPS with lubuntu-desktop and xrdp, and received the same errors. I can't put my finger on why chromium on these fresh installs is corrupt.

---

### Post by steeldriver on 2013-12-19
Do you know how up to date the VPS packages are? particularly gtk / gdk libs

```

uname -a

cat /etc/lsb-release

dpkg -l | egrep 'g[td]k'

```

... clutching at straws here

---

### Post by genivasla on 2013-12-19
Here are the results from those commands on the most recent lubuntu install...

```
Linux host.lubuntutestxxx.com 3.5.0-44-generic #67~precise1-Ubuntu SMP Wed Nov 13 16:16:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"



```

```
ii  apport-gtk                             2.0.1-0ubuntu17.6                                                                                                                                                       GTK+ frontend for the apport crash report systemii  gir1.2-dbusmenu-gtk-0.4                0.6.2-0ubuntu0.2                                                                                                                                                        typelib file for libdbusmenu-gtk4
ii  gir1.2-gdkpixbuf-2.0                   2.26.1-1                                                                                                                                                                GDK Pixbuf library - GObject-Introspection
ii  gir1.2-gtk-2.0                         2.24.10-0ubuntu6                                                                                                                                                        GTK+ graphical user interface library -- gir bindings
ii  gir1.2-gtk-3.0                         3.4.2-0ubuntu0.5                                                                                                                                                        GTK+ graphical user interface library -- gir bindings
ii  gir1.2-javascriptcoregtk-3.0           1.8.3-0ubuntu0.12.04.1                                                                                                                                                  GObject introspection data for the GTK+-based JavaScriptCore library
ii  gtk2-engines                           1:2.20.2-1ubuntu1                                                                                                                                                       theme engines for GTK+ 2.x
ii  gtk2-engines-murrine                   0.98.2-0ubuntu1                                                                                                                                                         cairo-based gtk+-2.0 theme engine
ii  gtk2-engines-pixbuf                    2.24.10-0ubuntu6                                                                                                                                                        pixbuf-based theme for GTK+ 2.x
ii  gtk3-engines-unico                     1.0.2-0ubuntu1                                                                                                                                                          Unico Gtk+ 3 theme engine
ii  ibus-gtk                               1.4.1-3ubuntu1                                                                                                                                                          Intelligent Input Bus - GTK+2 support
ii  ibus-gtk3                              1.4.1-3ubuntu1                                                                                                                                                          Intelligent Input Bus - GTK+3 support
ii  jockey-gtk                             0.9.7-0ubuntu7.11                                                                                                                                                       GNOME user interface and desktop integration for driver management
ii  libavahi-ui-gtk3-0                     0.6.30-5ubuntu2                                                                                                                                                         Avahi GTK+ User interface library for GTK3
ii  libcanberra-gtk3-0                     0.28-3ubuntu3                                                                                                                                                           GTK+ 3.0 helper for playing widget event sounds with libcanberra
ii  libcanberra-gtk3-module                0.28-3ubuntu3                                                                                                                                                           translates GTK3 widgets signals to event sounds
ii  libdbusmenu-gtk3-4                     0.6.2-0ubuntu0.2                                                                                                                                                        library for passing menus over DBus - GTK+ version
ii  libdbusmenu-gtk4                       0.6.2-0ubuntu0.2                                                                                                                                                        library for passing menus over DBus - GTK+ version
ii  libfm-gtk-data                         0.1.17-0ubuntu3.1                                                                                                                                                       file management support - common files
ii  libfm-gtk1                             0.1.17-0ubuntu3.1                                                                                                                                                       file management support - GTK+ GUI library
ii  libgdk-pixbuf2.0-0                     2.26.1-1                                                                                                                                                                GDK Pixbuf library
ii  libgdk-pixbuf2.0-common                2.26.1-1                                                                                                                                                                GDK Pixbuf library - data files
ii  libgdu-gtk0                            3.0.2-2ubuntu7                                                                                                                                                          GTK+ standard dialog library for libgdu
ii  libgtk-3-0                             3.4.2-0ubuntu0.5                                                                                                                                                        GTK+ graphical user interface library
ii  libgtk-3-bin                           3.4.2-0ubuntu0.5                                                                                                                                                        programs for the GTK+ graphical user interface library
ii  libgtk-3-common                        3.4.2-0ubuntu0.5                                                                                                                                                        common files for the GTK+ graphical user interface library
ii  libgtk2-perl                           2:1.223-1build3                                                                                                                                                         Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2.0-0                            2.24.10-0ubuntu6                                                                                                                                                        GTK+ graphical user interface library
ii  libgtk2.0-bin                          2.24.10-0ubuntu6                           programs for the GTK+ graphical user interface library
ii  libgtk2.0-common                       2.24.10-0ubuntu6                                                                                                                                                        common files for the GTK+ graphical user interface library
ii  libgtkmathview0c2a                     0.8.0-7                                                                                                                                                                 rendering engine for MathML documents
ii  libgtkspell0                           2.0.16-1ubuntu5                                                                                                                                                         a spell-checking addon for GTK's TextView widget
ii  libido3-0.1-0                          0.3.4-0ubuntu1                                                                                                                                                          Shared library providing extra gtk menu items for display in
ii  libindicate-gtk3                       0.6.92-0ubuntu1                                                                                                                                                         library for raising indicators via DBus - GTK+ bindings
ii  libjavascriptcoregtk-1.0-0             1.8.3-0ubuntu0.12.04.1                                                                                                                                                  Javascript engine library for GTK+
ii  libjavascriptcoregtk-3.0-0             1.8.3-0ubuntu0.12.04.1                                                                                                                                                  Javascript engine library for GTK+
ii  libnm-gtk-common                       0.9.4.1-0ubuntu2.3                                                                                                                                                      network management framework (common files for wifi and mobile)
ii  libnm-gtk0                             0.9.4.1-0ubuntu2.3                                                                                                                                                      network management framework (GNOME dialogs for wifi and mobile)
ii  libwebkitgtk-1.0-0                     1.8.3-0ubuntu0.12.04.1                                                                                                                                                  Web content engine library for GTK+
ii  libwebkitgtk-1.0-common                1.8.3-0ubuntu0.12.04.1                                                                                                                                                  Web content engine library for GTK+ - data files
ii  libwebkitgtk-3.0-0                     1.8.3-0ubuntu0.12.04.1                                                                                                                                                  Web content engine library for GTK+
ii  libwebkitgtk-3.0-common                1.8.3-0ubuntu0.12.04.1                                                                                                                                                  Web content engine library for GTK+ - data files
ii  lightdm-gtk-greeter                    1.1.5-0ubuntu1.1                                                                                                                                                        LightDM GTK+ Greeter
ii  python-aptdaemon.gtk3widgets           0.43+bzr805-0ubuntu9                                                                                                                                                    Python GTK+ 3 widgets to run an aptdaemon client
ii  python-gtk2                            2.24.0-3                                                                                                                                                                Python bindings for the GTK+ widget set
ii  software-properties-gtk                0.82.7.6                                                                                                                                                                manage the repositories that you install software from (gtk)
ii  transmission-gtk                       2.51-0ubuntu1.3                                                                                                                                                         lightweight BitTorrent client (GTK interface)



```

---

### Post by steeldriver on 2013-12-19
Oops somehow I missed that yours was a 64-bit platform - that is probably more significant than any package versions. The 2 boxes I tested on are 32-bit.

---

### Post by genivasla on 2013-12-19
My bad! I think I left the fact that these are running on 64 bit instances of Ubuntu. I don't see how that would be the issue though?

---

### Post by genivasla on 2013-12-20
I installed lubuntu on Virtualbox on my local machine, and everything works fine. Still having issues on the vnc.

I tried XRDP and noticed the error was the following when run as the user1 account. ```
Xlib extension &#8220;RANDR&#8221; missing on display ":10.0"
```  When I accessed the desktop as root, the error was: ```
Xlib extension &#8220;RANDR&#8221; missing on display ":10.0"
```.

This is slightly different from the error received when accessing via Tightvnc vrs XRDP: ```
Xlib extension &#8220;RANDR&#8221; missing on display ":1
``` 

I was also pointed to this possible explanation: [http://askubuntu.com/questions/220504/how-to-make-chromium-browser-start-on-vnc-display](http://askubuntu.com/questions/220504/how-to-make-chromium-browser-start-on-vnc-display). Unfortunately I haven't figured out how to create two config directories and run them separately.

---

### Post by steeldriver on 2013-12-20
FWIW I installed a 64-bit 12.04.3 server in a VirtualBox VM and then lxde-core + tightvncserver + chromium-browser as before and it all appeared to work fine - so it's not just a 64-bit versus 32-bit thing

I think the only thing you're doing that I haven't tried yet is starting the VNC server using init (I am opening a PuTTY session from the Win7 host, starting vncserver manually, and tunneling the VNC over SSH) - have you tried starting VNC manually (SSH tunnel optional) to see if that makes a difference?

---

### Post by genivasla on 2013-12-20
Just tried to start vnc manually with no luck. Used these commands. Maybe I'm doing it wrong.

```
[COLOR=#000000][FONT=Tahoma]sudo /etc/init.d/vncserver stop
[/FONT][/COLOR][COLOR=#464646][FONT=monospace]vncserver -geometry 1280x1024 -depth 16[/FONT][/COLOR]

```

---

### Post by steeldriver on 2013-12-20
I'm now starting mine using your init script as well - no difference from my side either

---

### Post by genivasla on 2013-12-20
Now that's really weird that you're not having any issues. I'm so confused!

---

### Post by genivasla on 2013-12-21
Small update... I reimaged the VPS with Ubuntu 10.04, installed lxde with tightvnc and everything is working fine. Did the same with Debian 7.2. so seems it has something to do with Ubuntu 12.04.

---

### Post by steeldriver on 2013-12-21
Just wondering... did you update / upgrade the original install system? I always do that before installing the lxde-core / tightvncserver / chromium-browser packages, maybe we have package versions that are different?

---

### Post by genivasla on 2013-12-21
Before running the installs I did run ```
apt-get update
apt-get upgrade
```

Is there another way to do this?

---

### Post by steeldriver on 2013-12-21
no that's right

I wonder if you're just hitting a memory limit? it's strange that it fails silently (apart from the Xlib RANDR extension, which I don't think is significant). Are you running any other processes on the VPS? I noticed in your (I'm assuming your) askubuntu Q that the VPS is only 528MB (are you sure about that? it's a funny number, usually it's a power of 2)

My 64-bit server VM is configured with 512MB and pretty much all of that gets eaten up i.e.


Freshly rebooted VM, no VNC server yet (just an SSH session using PuTTY from the Win7 host)
```

steeldriver@alice-vm2:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           490        151        339          0         13         76
-/+ buffers/cache:         61        429
Swap:          509          0        509

```

After starting the VNC server (geometry 1280x1024, depth 16)
```

steeldriver@alice-vm2:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           490        182        308          0         13         77
-/+ buffers/cache:         91        399
Swap:          509          0        509

```

Now let's start the browser
```

steeldriver@alice-vm2:~$ DISPLAY=:1 chromium-browser &
[1] 1692
steeldriver@alice-vm2:~$ Xlib:  extension "RANDR" missing on display ":1".

steeldriver@alice-vm2:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           490        328        162          0         14        175
-/+ buffers/cache:        139        351
Swap:          509          0        509
steeldriver@alice-vm2:~$

```

I initially tried that before rebooting the VM and got down in the 10s of MB free

---

### Post by genivasla on 2013-12-21
Yeah, that's my askubuntu post as well. I did mean 512, however I can adjust that up very easily on the fly (running on a cloud server). In fact I have tried by bumping up to 2gb of memory, but that didn't help. I'll test again just to double check. The memory limit thing was one of my first thoughts. I'm sure this is something very silly like that.

I also tried changing color depth in case that was causing the weird purple screen, but no luck there either.

---

### Post by steeldriver on 2013-12-21
Did we look at the vncserver log? it should be in ~/.vnc and will be called something like ~/.vnc/*machinename*:1.log (for display :1)

Although TBH I think it usually only contains server-side stuff, I would have thought X-client errors should go in ~/.xsession-errors and we already looked there

EDIT: wait - what weird purple screen? did I miss something? do you not get the regular blue lxde swoosh? What VNC client are you using?

---

### Post by genivasla on 2013-12-21
Bumped RAM up to 2gb, rebooted, restarted VNC and no changes there. 

Good thinking on the vnc log. There's some interesting stuff here that may point to some issues. I replaced my local IP with 11.11.111.111

```
21/12/13 12:05:41 Xvnc version TightVNC-1.3.921/12/13 12:05:41 Copyright (C) 2000-2007 TightVNC Group
21/12/13 12:05:41 Copyright (C) 1999 AT&T Laboratories Cambridge
21/12/13 12:05:41 All Rights Reserved.
21/12/13 12:05:41 See http://www.tightvnc.com/ for information on TightVNC
21/12/13 12:05:41 Desktop name 'X' (host.machinename.com:1)
21/12/13 12:05:41 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
21/12/13 12:05:41 Listening for VNC connections on TCP port 5901
Font directory '/usr/share/fonts/X11/Type1/' not found - ignoring
Font directory '/usr/share/fonts/X11/75dpi/' not found - ignoring
Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring
xrdb: No such file or directory
xrdb: can't open file '/home/user1/.Xresources'


21/12/13 12:05:49 Got connection from client 11.11.111.111
21/12/13 12:05:49 Using protocol version 3.8
21/12/13 12:05:49 Enabling TightVNC protocol extensions
21/12/13 12:05:53 Full-control authentication passed by 11.11.111.111
21/12/13 12:05:53 Using tight encoding for client 11.11.111.111
21/12/13 12:05:53 rfbProcessClientNormalMessage: ignoring unknown encoding 16
21/12/13 12:05:53 Using image quality level 6 for client 11.11.111.111
21/12/13 12:05:53 rfbProcessClientNormalMessage: ignoring unknown encoding -223
21/12/13 12:05:53 Enabling LastRect protocol extension for client 11.11.111.111
21/12/13 12:05:53 Enabling cursor position updates for client 11.11.111.111
21/12/13 12:05:53 Enabling full-color cursor updates for client 11.11.111.111
21/12/13 12:05:53 Pixel format for client 11.11.111.111:
21/12/13 12:05:53   32 bpp, depth 24, little endian
21/12/13 12:05:53   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0

```

---

### Post by steeldriver on 2013-12-21
That's all pretty normal I think - the only thing I don't see in mine is the xrdb error (because my ~/.vnc/xstartup tests before trying to open it). My client IP is 127.0.0.1 because the connection is tunneled.

```

steeldriver@alice-vm2:~$ cat ~/.vnc/alice-vm2\:1.log
21/12/13 11:33:30 Xvnc version TightVNC-1.3.9
21/12/13 11:33:30 Copyright (C) 2000-2007 TightVNC Group
21/12/13 11:33:30 Copyright (C) 1999 AT&T Laboratories Cambridge
21/12/13 11:33:30 All Rights Reserved.
21/12/13 11:33:30 See http://www.tightvnc.com/ for information on TightVNC
21/12/13 11:33:30 Desktop name 'X' (alice-vm2:1)
21/12/13 11:33:30 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
21/12/13 11:33:30 Listening for VNC connections on TCP port 5901
Font directory '/usr/share/fonts/X11/Type1/' not found - ignoring
Font directory '/usr/share/fonts/X11/75dpi/' not found - ignoring
Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring

21/12/13 11:33:53 Got connection from client 127.0.0.1
21/12/13 11:33:53 Using protocol version 3.8
21/12/13 11:33:53 Enabling TightVNC protocol extensions
21/12/13 11:33:57 Full-control authentication passed by 127.0.0.1
21/12/13 11:33:57 Using tight encoding for client 127.0.0.1
21/12/13 11:33:57 rfbProcessClientNormalMessage: ignoring unknown encoding 16
21/12/13 11:33:57 Using image quality level 6 for client 127.0.0.1
21/12/13 11:33:57 rfbProcessClientNormalMessage: ignoring unknown encoding -223
21/12/13 11:33:57 Enabling LastRect protocol extension for client 127.0.0.1
21/12/13 11:33:57 Enabling cursor position updates for client 127.0.0.1
21/12/13 11:33:57 Enabling full-color cursor updates for client 127.0.0.1
21/12/13 11:33:57 Pixel format for client 127.0.0.1:
21/12/13 11:33:57   32 bpp, depth 24, little endian
21/12/13 11:33:57   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
21/12/13 12:10:59 KbdAddEvent: unknown KeySym 0xff61 - allocating KeyCode 89

```

```

steeldriver@alice-vm2:~$ cat ~/.vnc/xstartup
#!/bin/sh

#Uncommment this line if using Gnome and your keyboard mappings are incorrect.
#export XKL_XMODMAP_DISABLE=1

[B]# Load X resources (if any)
if [ -r "$HOME/.Xresources" ]
then
        xrdb "$HOME/.Xresources"
fi[/B]

export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession
lxterminal &
/usr/bin/lxsession -s LXDE &

```

---

### Post by genivasla on 2013-12-21
I used your .vnc/startup code just to check, and no go. Maybe this part of the .vnc log is significant?

```
[COLOR=#000000][FONT=Ubuntu Mono]xrdb: No such file or directory
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]xrdb: can't open file '/home/user1/.Xresources'[/FONT][/COLOR]
```

---

