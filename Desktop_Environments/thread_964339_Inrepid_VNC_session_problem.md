---
title: "Inrepid VNC session problem"
date: 2008-10-30
forum: Desktop Environments
---

### Post by Underpants on 2008-10-30
I have always setup VNC to be running on the console of my ubuntu systems. It seems like every new release something tiny in my config needs to be changed to make it work.



Then I add these lines of code:
```

/usr/bin/x11vnc -localhost -o /var/log/x11vnc.log -forever -bg

```

and add KillInitClients=false to /etc/gdm/gdm.conf


I can cold boot the system, connect via SSH with tunneling and connect to the login screen with my VNC client, login, and then be presented with the desktop. Lather, rinse, repeat. 


Anyway, Now, with Inrepid I get the login screen, but x11vnc drop right after the login and appears to not be running. 

Here is my gdm config


```

#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George



PATH=/usr/bin/X11:/usr/X11R6/bin:/opt/X11R6/bin:$PATH
OLD_IFS=$IFS



/usr/bin/x11vnc -localhost -o /var/log/x11vnc.log -forever -bg
KillInitClients=false

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

sysresources=/etc/X11/Xresources

# merge in defaults
if [ -f "$sysresources" ]; then
    xrdb -merge "$sysresources"
fi

sysmodmap=/etc/X11/Xmodmap

XMODMAP=`gdmwhich xmodmap`
if [ x$XMODMAP != x ] ; then
  if [ x$GDM_PARENT_DISPLAY = x ]; then
    if [ -f $sysmodmap ]; then
      $XMODMAP $sysmodmap
    fi
  else
    ( DISPLAY=$GDM_PARENT_DISPLAY XAUTHORITY=$GDM_PARENT_XAUTHORITY $XMODMAP -pke ) | $XMODMAP -
  fi

  #
  # Switch Sun's Alt and Meta mod mappings
  #

  UNAME=`gdmwhich uname`
  PROCESSOR=`$UNAME -p`
  if [ x$PROCESSOR = xsparc ]; then
    if $XMODMAP | /usr/bin/grep mod4 | /usr/bin/grep Alt > /dev/null 2>/dev/null
    then
      $XMODMAP -e "clear Mod1" \
               -e "clear Mod4" \
               -e "add Mod1 = Alt_L" \
               -e "add Mod1 = Alt_R" \
               -e "add Mod4 = Meta_L" \
               -e "add Mod4 = Meta_R"
    fi
  fi
fi

SETXKBMAP=`gdmwhich setxkbmap`
if [ x$SETXKBMAP != x ] ; then
  # FIXME: is this all right?  Is this completely on crack?
  # What this does is move the xkb configuration from the GDM_PARENT_DISPLAY
  # FIXME: This should be done in code.  Or there must be an easier way ...
  if [ -n "$GDM_PARENT_DISPLAY" ]; then
    XKBSETUP=`( DISPLAY=$GDM_PARENT_DISPLAY XAUTHORITY=$GDM_PARENT_XAUTHORITY $SETXKBMAP -v )`
    if [ -n "$XKBSETUP" ]; then
      XKBKEYMAP=`echo "$XKBSETUP" | grep '^keymap' | awk '{ print $2 }'`
      XKBTYPES=`echo "$XKBSETUP" | grep '^types' | awk '{ print $2 }'`
      XKBCOMPAT=`echo "$XKBSETUP" | grep '^compat' | awk '{ print $2 }'`
      XKBSYMBOLS=`echo "$XKBSETUP" | grep '^symbols' | awk '{ print $2 }'`
      XKBGEOMETRY=`echo "$XKBSETUP" | grep '^geometry' | awk '{ print $2 }'`
      if [ -n "$XKBKEYMAP" ]; then
        $SETXKBMAP -keymap "$XKBKEYMAP"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" -a -n "$XKBGEOMETRY" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS" -geometry "$XKBGEOMETRY"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS"
      elif [ -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -symbols "$XKBSYMBOLS"
      fi
    fi
  fi
fi

exit 0

```

---

### Post by Underpants on 2008-10-30
> **Underpants said:**
> I have always setup VNC to be running on the console of my ubuntu systems. It seems like every new release something tiny in my config needs to be changed to make it work.



Then I add these lines of code:
```

/usr/bin/x11vnc -localhost -o /var/log/x11vnc.log -forever -bg

```

and add KillInitClients=false to /etc/gdm/gdm.conf


I can cold boot the system, connect via SSH with tunneling and connect to the login screen with my VNC client, login, and then be presented with the desktop. Lather, rinse, repeat. 


Anyway, Now, with Inrepid I get the login screen, but x11vnc drop right after the login and appears to not be running. 

Here is my gdm config


```

#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George



PATH=/usr/bin/X11:/usr/X11R6/bin:/opt/X11R6/bin:$PATH
OLD_IFS=$IFS



/usr/bin/x11vnc -localhost -o /var/log/x11vnc.log -forever -bg
KillInitClients=false

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

sysresources=/etc/X11/Xresources

# merge in defaults
if [ -f "$sysresources" ]; then
    xrdb -merge "$sysresources"
fi

sysmodmap=/etc/X11/Xmodmap

XMODMAP=`gdmwhich xmodmap`
if [ x$XMODMAP != x ] ; then
  if [ x$GDM_PARENT_DISPLAY = x ]; then
    if [ -f $sysmodmap ]; then
      $XMODMAP $sysmodmap
    fi
  else
    ( DISPLAY=$GDM_PARENT_DISPLAY XAUTHORITY=$GDM_PARENT_XAUTHORITY $XMODMAP -pke ) | $XMODMAP -
  fi

  #
  # Switch Sun's Alt and Meta mod mappings
  #

  UNAME=`gdmwhich uname`
  PROCESSOR=`$UNAME -p`
  if [ x$PROCESSOR = xsparc ]; then
    if $XMODMAP | /usr/bin/grep mod4 | /usr/bin/grep Alt > /dev/null 2>/dev/null
    then
      $XMODMAP -e "clear Mod1" \
               -e "clear Mod4" \
               -e "add Mod1 = Alt_L" \
               -e "add Mod1 = Alt_R" \
               -e "add Mod4 = Meta_L" \
               -e "add Mod4 = Meta_R"
    fi
  fi
fi

SETXKBMAP=`gdmwhich setxkbmap`
if [ x$SETXKBMAP != x ] ; then
  # FIXME: is this all right?  Is this completely on crack?
  # What this does is move the xkb configuration from the GDM_PARENT_DISPLAY
  # FIXME: This should be done in code.  Or there must be an easier way ...
  if [ -n "$GDM_PARENT_DISPLAY" ]; then
    XKBSETUP=`( DISPLAY=$GDM_PARENT_DISPLAY XAUTHORITY=$GDM_PARENT_XAUTHORITY $SETXKBMAP -v )`
    if [ -n "$XKBSETUP" ]; then
      XKBKEYMAP=`echo "$XKBSETUP" | grep '^keymap' | awk '{ print $2 }'`
      XKBTYPES=`echo "$XKBSETUP" | grep '^types' | awk '{ print $2 }'`
      XKBCOMPAT=`echo "$XKBSETUP" | grep '^compat' | awk '{ print $2 }'`
      XKBSYMBOLS=`echo "$XKBSETUP" | grep '^symbols' | awk '{ print $2 }'`
      XKBGEOMETRY=`echo "$XKBSETUP" | grep '^geometry' | awk '{ print $2 }'`
      if [ -n "$XKBKEYMAP" ]; then
        $SETXKBMAP -keymap "$XKBKEYMAP"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" -a -n "$XKBGEOMETRY" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS" -geometry "$XKBGEOMETRY"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS"
      elif [ -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -symbols "$XKBSYMBOLS"
      fi
    fi
  fi
fi

exit 0

```


If I add KillInitClients=True to the gdm.conf file the VNC session disconnects are entering a password. I can reconnect, and I am prompted for the username and password again. 

If I connect to the login screen with VNC and login to the console at the actual computer, VNC will stay connected, and bring me to the desktop.... bonkers.

---

### Post by krunge on 2008-10-31
> **Underpants said:**
> 
and add KillInitClients=false to /etc/gdm/gdm.conf


I can cold boot the system, connect via SSH with tunneling and connect to the login screen with my VNC client, login, and then be presented with the desktop. Lather, rinse, repeat. 


Anyway, Now, with Inrepid I get the login screen, but x11vnc drop right after the login and appears to not be running. 


Maybe you need the KillInitClients line in 'gdm.conf-custom' too.

[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)

---

