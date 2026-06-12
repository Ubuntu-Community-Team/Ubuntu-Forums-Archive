---
title: "Can't start xfce"
date: 2005-07-20
forum: Desktop Environments
---

### Post by Karlos on 2005-07-20
when I try to fire up xfce a panel appears saying xsession error

the report goes as follows

/usr/bin/startxfce4: X Server already running on display : 0

/bin/sh: /etc/xdg/xfce4/xintirc: No such file or directory

I have tried purging and removing and re-installing everything to do with xfce and menu-xdg and menu (just in case) but still no luck.! ](*,) 

does anyone know what the relevant rc file should look like (roughly) so that I can attempt to put it back

/etc/xdg/xfce4/xinitrc

I believe that's what I'm looking for

regards

Karlos

---

### Post by wixtech on 2005-07-20
Sorry to hear about your problem.  I am a happy XFCE - Hoary user and I can empathize.  I have provided my xinitrc below, good luck.

```

#!/bin/sh
#
# Copyright (c) 2004-2005 os-cillation
# Copyright (c) 2004-2005 The Xfce development team
#

# fix broken $UID on some system...
if test "x$UID" = "x"; then
        UID=`id -u`
fi

# make sure that $XFCE4HOME is set
if test x"$XDG_CONFIG_HOME" = x""; then
        XFCE4HOME="$HOME/.config/xfce4"
else
        XFCE4HOME="$XDG_CONFIG_HOME/xfce4"
fi
export XFCE4HOME

# create the required dirs
mkdir -p "$XFCE4HOME/mcs_settings"
mkdir -p "$XFCE4HOME/panel"
mkdir -p "$XFCE4HOME/xffm"
mkdir -p "$XFCE4HOME/xfwm4"

# create temp file for X resources
XRESOURCES=`mktemp /tmp/xrdb.XXXXXX`

# Has to go prior to merging Xft.xrdb, as its the "Defaults" file
test -r $HOME/.Xdefaults && cat $HOME/.Xdefaults >> $XRESOURCES

# Check if the user wants to override the above defaults (set by
# mcs ui plugin)
if test -r $XFCE4HOME/Xft.xrdb; then
        cat $XFCE4HOME/Xft.xrdb >> $XRESOURCES
else
        # Those are fallback settings, use the ui plugin to change it
        # or add your overrides to ~/.Xresources
        # Xft DPI: 96
        # Xft.hintstyle: hintnone/hintslight/hintmedium/hintfull
        # Xft hinting: 1/0
cat >> $XRESOURCES << EOF
Xft.dpi: 96
Xft.hinting: 1
Xft.hintstyle: hintmedium
EOF
fi

# ~/.Xresources contains overrides to the above
test -r $HOME/.Xresources && cat $HOME/.Xresources >> $XRESOURCES

# load all X resources
xrdb -nocpp -merge $XRESOURCES
rm -f $XRESOURCES

# load local modmap
test -r $HOME/.Xmodmap && xmodmap $HOME/.Xmodmap

# run setup scripts
for script in /etc/xdg/xfce4/xinit.d/*; do
        test -x ${script} && ${script}
done

# Launch xscreensaver (if available), but only as non-root user
test $UID -gt 0 -a -z "$VNCSESSION" && xscreensaver -no-splash &

# Use ssh-agent if installed.  Run it separately so it populates the
# environment here, so we can clean it up later.
sshagent=`which ssh-agent`
if test "$sshagent" -a "x$sshagent" != "xno"; then
        eval `$sshagent`
fi

# use dbus-launch if installed
dbuslaunch=`which dbus-launch`
case "x$dbuslaunch" in
        xno*)
                unset dbuslaunch
                ;;
esac

# Run xfce4-session if installed
xfcesm=`which xfce4-session`
case "x$xfcesm" in
        x|xno*)
                ;;
        *)
                $dbuslaunch $xfcesm
                test -n "$SSH_AGENT_PID" && eval `$sshagent -k`
                exit 0
                ;;
esac

# this is only necessary when running w/o xfce4-session
xsetroot -solid black -cursor_name watch

# or use old-fashioned startup script otherwise

# Start ssh-agent if available
test -n "$sshagent" && eval `$sshagent`

xfce-mcs-manager
xfwm4 --daemon

# Start-up stuff from ~/Desktop/Autostart directory, if it exists
# (as it seems to be the new standard)
if test -d "$HOME/Desktop/Autostart"; then
  for i in `ls -1 -L ${HOME}/Desktop/Autostart/ 2>/dev/null`; do
    if test -x $HOME/Desktop/Autostart/$i; then
      $HOME/Desktop/Autostart/$i &
    fi
  done
fi

xftaskbar4&
xfdesktop&
xfcalendar &

panel=`which xfce4-panel`
case "x$panel" in
        x|xno*)
                ;;
        *)
                $panel
                ret=$?
                while test $ret -ne 0; do
                        xmessage -center -file - -timeout 20 -title Error <<EOF
A crash occured in the panel
Please report this to the xfce4-dev@xfce.org list
Meanwhile the panel will be restarted
EOF
                        cat >&2 <<EOF
A crash occured in the panel
Please report this to the xfce4-dev@xfce.org list
Meanwhile the panel will be restarted
EOF
                        $panel
                        ret=$?
                done
                ;;
esac

test -n "$SSH_AGENT_PID" && eval `$sshagent -k`

xsetroot -bg white -fg red  -solid black -cursor_name watch
```

---

### Post by Karlos on 2005-07-20
Many thanks

I'll let you know how I get on

---

