---
title: "Why is AWN starting up in openbox on its own?"
date: 2008-08-17
forum: Desktop Environments
---

### Post by cchung85 on 2008-08-17
Hey guys, I can't figure out why AWN is booting up when I start Openbox, it's not running in the background either, it's showing up on pypanel.
This is my autostart file, could someone please help me me out? I'd rather it either not show up at all at start up or start up in the background. I can't figure out why it's starting up when I didn't configure it to...

Any input would be great, thanks.


"
# This shell script is run before Openbox launches.
# Environment variables set here are passed to the Openbox session.

# Set a background color
BG=""
if which hsetroot >/dev/null; then
    BG=hsetroot
else
    if which esetroot >/dev/null; then
	BG=esetroot
    else
	if which xsetroot >/dev/null; then
	    BG=xsetroot
	fi
    fi
fi
test -z $BG || $BG -solid "#303030"

# D-bus
if which dbus-launch >/dev/null && test -z "$DBUS_SESSION_BUS_ADDRESS"; then
       eval `dbus-launch --sh-syntax --exit-with-session`
fi

# Make GTK apps look and behave how they were set up in the gnome config tools
if test -x /usr/libexec/gnome-settings-daemon >/dev/null; then
  /usr/libexec/gnome-settings-daemon &
elif which gnome-settings-daemon >/dev/null; then
  gnome-settings-daemon &
# Make GTK apps look and behave how they were set up in the XFCE config tools
elif which xfce-mcs-manager >/dev/null; then
  xfce-mcs-manager n &
fi

# Preload stuff for KDE apps
if which start_kdeinit >/dev/null; then
  LD_BIND_NOW=true start_kdeinit --new-startup +kcminit_startup &
fi

# Run XDG autostart things.  By default don't run anything desktop-specific
# See xdg-autostart --help more info
DESKTOP_ENV=""
if which /usr/lib/openbox/xdg-autostart >/dev/null; then
  /usr/lib/openbox/xdg-autostart $DESKTOP_ENV
fi

(sleep 3 && pypanel) &

xcompmgr &

nm-applet &

gnome-volume-manager &
"

---

### Post by cchung85 on 2008-08-31
Anyone? Please?

---

