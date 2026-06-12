---
title: "My ubuntu sometimes automatically logout after installing openbox"
date: 2014-03-02
forum: Desktop Environments
---

### Post by boy_toast on 2014-03-02
i got this error on my log, it keep logout automatically 
already reinstalled openbox, but this happened again :(
```
ERROR: apport (pid 26391) Sun Mar  2 20:57:36 2014: gdbus call error: Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

ERROR: apport (pid 26391) Sun Mar  2 20:57:36 2014: debug: session gdbus call: 
ERROR: apport (pid 26391) Sun Mar  2 20:57:36 2014: this executable already crashed 2 times, ignoring
ERROR: apport (pid 28921) Sun Mar  2 20:59:46 2014: called for pid 26598, signal 6
ERROR: apport (pid 28921) Sun Mar  2 20:59:46 2014: executable: /usr/bin/openbox (command line "/usr/bin/openbox --startup /usr/lib/openbox/openbox-autostart\ OPENBOX")
ERROR: apport (pid 28921) Sun Mar  2 20:59:46 2014: gdbus call error: Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

ERROR: apport (pid 28921) Sun Mar  2 20:59:46 2014: debug: session gdbus call: 
ERROR: apport (pid 28921) Sun Mar  2 20:59:46 2014: this executable already crashed 2 times, ignoring

```

---

### Post by phidia on 2014-03-04
I think you need to look at the configuration guide for openbox from [this Ubuntu page]("https://help.ubuntu.com/community/Openbox").

---

### Post by vasa1 on 2014-03-04
If you're not too familiar with how things work but still want to use Openbox, then it maybe better if you do a clean install of a distro that has Openbox as window manager by default. The official *buntu flavor with Openbox as window manager is Lubuntu. Then, there are quite a few other distros using Openbox as the window manager but they may need more experience with setting things up.

From what I gather, setting Openbox as window manager on a distro that doesn't have it by default is not recommended for newish users (or for users who want something working out of the box).

---

### Post by Jordan_Cameron on 2014-03-05
Openbox takes time and care to setup.  It's not like gnome or kde where you install it, log in and voila you're done.  It's just the window manager.  You also need to setup a compistor (if you want some effects), a wallpaper manager, a taskbar (tint2 is popular for this) along with any other things you would like, including a menu manager (such as obmenu).  If you want to get a feel for what openbox is like, check out LXDE.  It's a pre-configured Openbox environment.

Remember, Openbox is just a window manager, so it doesn't handle desktop drawing or file management.  That is all done with other apps added to your openbox install.

---

### Post by Portaro on 2014-03-05
HUm I use OPenbox on my buntu with Fluxbox, Gnome 3.2 , and Lubuntu desktop and I dont have any problem on my OPenbox I config the autostart /user /path  and other things.

MY autostart OPenbox file in the path that your log give a crash error is it -
/usr/lib/openshot/
> #!/bin/sh

# Set a background color
BG=""
if which hsetroot >/dev/null; then
  BG=hsetroot
elif which esetroot >/dev/null; then
  BG=esetroot
elif which xsetroot >/dev/null; then
  BG=xsetroot
fi
test -z $BG || $BG -solid "#303030"

GLOBALAUTOSTART="/etc/xdg/openbox/autostart"
AUTOSTART="${XDG_CONFIG_HOME:-"$HOME/.config"}/openbox/autostart"

# Run the global openbox autostart script
if test -f $GLOBALAUTOSTART; then
    sh $GLOBALAUTOSTART
elif test -f $GLOBALAUTOSTART.sh; then
    sh $GLOBALAUTOSTART.sh
fi

# Run the user openbox autostart script
if test -f $AUTOSTART; then
    sh $AUTOSTART
elif test -f $AUTOSTART.sh; then
    sh $AUTOSTART.sh
fi

# Run the XDG autostart stuff.  These are found in /etc/xdg/autostart and
# in $HOME/.config/autostart.  This requires PyXDG to be installed.
# See openbox-xdg-autostart --help for more details.
/usr/lib/openbox/openbox-xdg-autostart "$@"

In the place /usr/lib/openbox 
i have two files one - the above autostart file and other called 
**openbox-xdg-autostart** -> you have a similar file?

Is the only idea I had.

I also recommend this distro that is based on Ubuntu but by deafult with Openbox -
[http://gobangos.sourceforge.net/](http://gobangos.sourceforge.net/)

---

