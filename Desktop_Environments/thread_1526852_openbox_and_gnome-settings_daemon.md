---
title: "openbox and gnome-settings daemon"
date: 2010-07-08
forum: Desktop Environments
---

### Post by lautarop on 2010-07-08
Ok, now i have this problem:

I installed lucid, I installed openbox
I want to set a gtk2 theme, but the gnome-settings-daemon is not letting me do it.

So, I edit the autostart.sh under my ./config/openbox folder, and remove these lines:

[PHP]# Make GTK apps look and behave how they were set up in the gnome config tools
if test -x /usr/libexec/gnome-settings-daemon >/dev/null; then
  /usr/libexec/gnome-settings-daemon &
elif which gnome-settings-daemon >/dev/null; then
  gnome-settings-daemon &
[/PHP]

Then, if I reboot, I get the error that ubuntu has to load on low graphics mode; i quickly go to terminal mode, edit the autostart.sh back to how it was before, and I cant sign in ok.
[B]
What should I do? 
How can I remove the gnome-settings-daemon?[/B]

---

### Post by launchy on 2010-07-13
have u tried installing lxappearance from synaptics? its a gui for selecting gtk themes and icons for openbox. just type "lxappearance" in the terminal to launch it.

---

### Post by urukrama on 2010-07-13
> **lautarop said:**
> [B]
What should I do? 
How can I remove the gnome-settings-daemon?[/B]

I'm not sure what is going wrong on your system. Can you post your full ~/.config/openbox/autostart.sh file?

For reference, here is mine which does not use gnome-settings-daemon:

```
#!/bin/sh 
# OpenOffice gtk theme
export OOO_FORCE_DESKTOP=gnome
# feh stores the last background in .fehbg 
sh ~/.fehbg &
thunar --daemon &
docker &
sleep 2 && lal &

```

If you don't use gnome-settings-daemon, you can set the Gtk theme in various ways. In case you need help with that, have a look [here]("http://urukrama.wordpress.com/openbox-guide/#Gtkthemes") for more info.

---

### Post by lautarop on 2010-07-13
> **urukrama said:**
> I'm not sure what is going wrong on your system. Can you post your full ~/.config/openbox/autostart.sh file?

For reference, here is mine which does not use gnome-settings-daemon:


If you don't use gnome-settings-daemon, you can set the Gtk theme in various ways. In case you need help with that, have a look [here]("http://urukrama.wordpress.com/openbox-guide/#Gtkthemes") for more info.



Here's mine

[PHP]# This shell script is run before Openbox launches.
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
DESKTOP_ENV="OPENBOX"
if which /usr/lib/openbox/xdg-autostart >/dev/null; then
  /usr/lib/openbox/xdg-autostart $DESKTOP_ENV
fi



gnome-keyring-daemon &
nm-applet &
xfce4-panel &
parcellite &
conky & sleep 60 &&
sh /bin/gcal.sh &[/PHP]



I tried removing the lines

[PHP]# Make GTK apps look and behave how they were set up in the gnome config tools
if test -x /usr/libexec/gnome-settings-daemon >/dev/null; then
  /usr/libexec/gnome-settings-daemon &
elif which gnome-settings-daemon >/dev/null; then
  gnome-settings-daemon &

[/PHP]

But then, after i reboot, I get the low graphics mode error.

If I put that line again, everything is fine.



ps: (I was able to set the gtk theme trough the gnome-editor; still, I want to see if I can get this working without having to run gnome-settings-daemon)

---

