---
title: "VNC in 14.04 - Amazon instance"
date: 2014-05-04
forum: Desktop Environments
---

### Post by one2wonder on 2014-05-04
I set up an amazon instance.  I installed ubuntu desktop via apt-get.  I installed VNC4SERVER.  I tried a plethora of guides online for configuring my /.vnc/xstartup file.  I can connect over my ssh tunnel, but all I get is a grey screen and a cursor.  Here is the current contents of my config file.  If anyone can help it would be greatly appreciated.

#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# exec sh /etc/X11/xinit/xinitrc
gnome-session --session=gnome-classic &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
# x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
# x-window-manager &

---

### Post by jon51 on 2014-05-28
Same Problem ... any ideas?

---

### Post by steeldriver on 2014-05-28
What desktop sessions do you actually have installed (i.e. what are the contents of the /usr/share/xsessions directory)?

I'm not running 14.04 yet but afaik the classic desktop requires package gnome-session-flashback

---

### Post by jon51 on 2014-05-28
To answer your question:

gnome.desktop  gnome-fallback-compiz.desktop  gnome-fallback.desktop  ubuntu.desktop

I believe I have it tracked down to the following line:

exec /etc/X11/xinit/xinitrc 

when I have this line enable I get a grey checked screen ... when I have it commented out I get a terminal window.  

Should I have something else here?

The full file looks like:

!/bin/sh


# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
exec /etc/X11/xinit/xinitrc


[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &


gnome-session --session=gnome-classic &

---

### Post by jon51 on 2014-05-29
Any help in pointing me in the right direction?  I truly appreciate all help ...

---

### Post by steeldriver on 2014-05-29
The 'exec' command replaces the current shell with the given command - in other words, your xstartup is quitting (to /etc/X11/xinit/xinitrc) before it gets to your specified session.

Here's a minimal $HOME/.vnc/xstartup that should work provided you have a /usr/share/xsessions/gnome-classic.desktop - in 14.04, you will probably need to install gnome-shell-extensions or install gnome-session-fallback and replace gnome-classic by gnome-fallback. Sorry I'm not up to date with all the gnome forking.


```

#!/bin/sh

#Uncommment this line if using Gnome and your keyboard mappings are incorrect.
#export XKL_XMODMAP_DISABLE=1

# Load X resources (if any)
if [ -r "$HOME/.Xresources" ]
then
        xrdb "$HOME/.Xresources"
fi

gnome-session --session=gnome-classic &

```

Here's a more generic example that I use on a work server, which allows me to set a preferred session type - but fall back to another available session if that's unavailable

```

#!/bin/sh

MODE="lxde"

#Uncommment this line if using Gnome and your keyboard mappings are incorrect.
#export XKL_XMODMAP_DISABLE=1

# Load X resources (if any)
[ -r "$HOME/.Xresources" ] && xrdb "$HOME/.Xresources"

case $MODE in

xfce4)
    if which startxfce4 > /dev/null; then
        exec startxfce4 
    fi
    ;;

lxde)
    if which startlxde > /dev/null; then
        exec startlxde
    fi
    ;;

openbox)
    if which openbox-session > /dev/null; then
        exec openbox-session
    fi
    ;;

*)
    echo "Falling back to default minimal X session"
    ;;

esac

xsetroot -solid "#DAB082"
x-terminal-emulator -geometry "80x24+10+10" -ls -title " Desktop" &
x-window-manager &

```

---

### Post by jon51 on 2014-05-29
[COLOR=#000000]I have updated $HOME/.vnc/xstartup

And stopped trying to startx with sudo

I get X: user not authorized to run the X server, aborting[/COLOR]

---

### Post by jon51 on 2014-05-29
I have corrected the issue of not authorized by following the directions at:
[http://karuppuswamy.com/wordpress/2010/09/26/how-to-fix-x-user-not-authorized-to-run-the-x-server-aborting/](http://karuppuswamy.com/wordpress/2010/09/26/how-to-fix-x-user-not-authorized-to-run-the-x-server-aborting/)

By allowing anybody to start console

Now I am getting the fatal error while loading extension GLX like I was when I was trying to startx with sudo

---

### Post by jon51 on 2014-05-30
Just in case anyone else shows up needing a solution ...

I ended up installing KDE Desktop and was able to VNC to it with VNC4Server without a problem, I tried several variations of gnome and nothing ever seemed to work besides getting a terminal window.

Final .vnc/xstartup file looked like:

#!/bin/sh


# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
#exec sh /etc/X11/xinit/xinitrc


[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
#startx &


startkde &

---

