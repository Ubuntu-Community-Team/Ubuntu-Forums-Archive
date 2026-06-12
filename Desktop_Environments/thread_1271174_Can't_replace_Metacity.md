---
title: "Can't replace Metacity"
date: 2009-09-20
forum: Desktop Environments
---

### Post by tezer on 2009-09-20
Hi
I've got a problem trying to replace metacity with pekwm. It is not a pekwm specific problem - I had the same problem with xfwm4.
And now about the problem. It's simple - whatever I do metacity is still there.
Here is what I did:
1. Created .gnomerc:
```
export WINDOW_MANAGER=/usr/local/bin/pekwm
```
2. Changed /usr/bin/gnome-wm putting "pekwm" whereever possible
```
#!/bin/sh

# The user can specify his prefered WM by setting the WINDOW_MANAGER
# environment variable or setting the
# /desktop/gnome/applications/window_manager/default gconf key.
#
# If this is not set, we search a list of known windowmanagers and use
# the first one that is found in the users's PATH
#
# NOTE: DON'T USE THIS.  Please have your window manager install
# a desktop file and change the gconf key
# /desktop/gnome/session/required_components/windowmanager

# sm-client-id value
SMID=
# default-wm value
DEFWM=

#read in the arguments
GET=
for n in "$@" ; do
  case "$GET" in
    smid)
      SMID=$n
      GET=
      ;;
    defwm)
      DEFWM=$n
      GET=
      ;;
    *)
      case "$n" in
        --sm-client-id)
          GET=smid
          ;;
        --default-wm)
          GET=defwm
          ;;
      esac
      ;;
  esac
done

# Get previously set window manager in gconf
if [ ! "$DEFWM" ]; then
  DEFWM=`gconftool-2 -g /desktop/gnome/applications/window_manager/default 2>/dev/null`
fi

# special case handling for dapper upgrades (this runs only once after the upgrade)
if [ -z "$DEFWM" ] && [ -f /var/lib/gnome-session/dapper-upgrade ]; then
    gconftool-2 -s /desktop/gnome/applications/window_manager/default /usr/bin/metacity --type string
    DEFWM=/usr/bin/metacity
fi

# If not exist, set to pekwm (if available) 
if [ ! -x "$DEFWM" ]; then
    if [ -x "/usr/local/bin/pekwm" ]; then
	gconftool-2 -s /desktop/gnome/applications/window_manager/default /usr/local/bin/pekwm --type string
	DEFWM=/usr/local/bin/pekwm
    elif [ -x "/usr/local/bin/pekwm" ]; then
	gconftool-2 -s /desktop/gnome/applications/window_manager/default /usr/local/bin/pekwm --type string
	DEFWM=/usr/local/bin/pekwm
    else
	unset DEFWM
    fi
fi

# WINDOW_MANAGER overrides all
if [ -z "$WINDOW_MANAGER" ] ; then
    WINDOW_MANAGER=`gconftool-2 --get /desktop/gnome/session/required_components/windowmanager 2> /dev/null`
fi

# Avoid looping if the session configuration tells us to use gnome-wm or if
# the user forces gnome-wm via WINDOW_MANAGER
if [ "x$WINDOW_MANAGER" = "xgnome-wm" ]; then
  WINDOW_MANAGER=""
fi

if [ -z "$WINDOW_MANAGER" ] ; then
  # Create a list of window manager we can handle, trying to only use the
  # compositing ones when it makes sense

  xdpyinfo 2> /dev/null | grep -q "^ *Composite$" 2> /dev/null
  IS_X_COMPOSITED=$?

  KNOWN_WM="pekwm sawfish sawmill enlightenment icewm wmaker fvwm2 qvwm fvwm twm kwm"
  if [ $IS_X_COMPOSITED -eq 0 ] ; then
    KNOWN_WM="compiz beryl $KNOWN_WM"
  fi
  # pekwm is still the default wm in GNOME
  KNOWN_WM="pekwm $KNOWN_WM"

  OLDIFS=$IFS
  if [ -z "$DEFWM" -o "x$DEFWM" = "xgnome-wm" ]; then
    for wm in $KNOWN_WM ; do
      IFS=":"
      for dir in $PATH ; do
	if [ -x "$dir/$wm" ] ; then
	  WINDOW_MANAGER="$dir/$wm"
    	  break 2
	fi
      done
      IFS=$OLDIFS
    done
  else
    WINDOW_MANAGER=$DEFWM
  fi
  IFS=$OLDIFS
fi

# If no window manager can be found, we default to xterm

if [ -z "$WINDOW_MANAGER" ] ; then
  echo "WARNING: No window manager can be found."
  WINDOW_MANAGER=`readlink /etc/alternatives/x-terminal-emulator 2>/dev/null`
fi

# Now create options OPT1, OPT2 and OPT3 based on the windowmanager used
OPT1=
OPT2=
OPT3=
OPT4=
if [ ! -z "$SMID" ] ; then
  case `basename $WINDOW_MANAGER` in
    sawfish|sawmill|pekwm|openbox)
      OPT1=--sm-client-id=$SMID
      ;;
    openbox|enlightenment|e16)
      OPT1=--sm-client-id
      OPT2=$SMID
      ;;
    twm)
      OPT1=-clientId
      OPT2=$SMID
      ;;
    lwm)
      OPT1=-s
      OPT2=$SMID
      ;;
    fvwm)
      OPT1=-i
      OPT2=$SMID
      ;;
    compiz)
      OPT1=--sm-client-id
      OPT2=$SMID
      ;;
    beryl)
      OPT1=--sm-client-id
      OPT2=$SMID
      ;;
    #FIXME: add all other windowmanagers here with their proper options
  esac
fi

case `basename $WINDOW_MANAGER` in
  beryl)
    emerald &
    ;;
esac

# Store the selected WM with gconf
gconftool-2 -t string -s /desktop/gnome/applications/window_manager/current "$WINDOW_MANAGER"

exec $WINDOW_MANAGER $OPT1 $OPT2 $OPT3 $OPT4

echo "ERROR: No window manager could run!"
```

3. Tried saving session with pekwm running.

Nothing helped. Every time I load Gnome session it starts with metacity. Pekwm easily replace metacity with "pekwm --replace" and works fine, but I can't make it a default WM.
The only possible way (wich I already tried with other WM) is to uninstall metacity. But it goes together with ubuntu-desktop.
Any suggestions how to replace metacity?

Thanks a lot in advance.

---

### Post by tezer on 2009-09-21
Here is an update.
I tried to replace "metacity" to "pekwm" in desktop/gnome/session/required_components/windowmanager" (gconf-editor).
The output is absence of any window decorations at all! It seems that metacity is gone, but pekwm isn't there.
There were also some 'side effects". Occasionally (but rather often) oowriter was running at the start up (I double-checked autostart, oowriter isn't there). Gnome-panels are moved and some applets are in wrong places. Conky is also a little bit moved down.

It's really strange...

---

### Post by kerry_s on 2009-09-21
what i do when i want to replace a program is create a script in ~/bin with the exact name as the program i'm trying to replace. the ~/bin is always checked before /usr/bin.

example:

**gedit ~/bin/metacity**

put:
[B]#!/bin/sh
peckwm[/B]

edit: never mind just tried it, don't work cause metacity is called by the full path "/usr/bin/metacity" so you would have to replace that with the script.

---

### Post by tezer on 2009-09-21
**kerry_s**, thanks for the idea, but it doesn't work. I did as you advised and replaced the /usr/bin/metacity with the script. After loading there was no ANY window decoration at all. I had to start WM manually...

So I returned the desktop/gnome/session/required_components/windowmanager key to pekwm, so that metacity does not load and in autostart added "pekwm --replace". Now it starts in pekwm.
Any better ideas? Or should I consider it solved?

PS Why did they chose metacity to be a default WM??? Why is it so difficult to get rid of it?

---

### Post by theZoid on 2009-09-21
> **tezer said:**
> **kerry_s**, thanks for the idea, but it doesn't work. I did as you advised and replaced the /usr/bin/metacity with the script. After loading there was no ANY window decoration at all. I had to start WM manually...

So I returned the desktop/gnome/session/required_components/windowmanager key to pekwm, so that metacity does not load and in autostart added "pekwm --replace". Now it starts in pekwm.
Any better ideas? Or should I consider it solved?

PS Why did they chose metacity to be a default WM??? Why is it so difficult to get rid of it?

that's the only way I've ever been able to replace the window manager, i.e. through the xxxxxx --replace in startup applications.  the gnomerc doesn't work but in older releases.  Solved :)

---

### Post by tezer on 2009-09-22
Well, it doesn't look like "the Linux way", but let's consider it solved...

PS. Still what makes metacity so difficult to get rid of???

---

