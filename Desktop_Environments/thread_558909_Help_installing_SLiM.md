---
title: "Help installing SLiM"
date: 2007-09-24
forum: Desktop Environments
---

### Post by Antilles on 2007-09-24
I installed plain XFCE over a server install of Ubuntu in an attempt to have a more streamlined install than vanilla Xubuntu.  In service of this goal I went with XDM as my login manager as opposed to GDM or KDM.  Recently I decided to try out the [Simple Login Manager]("http://slim.berlios.de/manual.php") (SLiM) but I'm having trouble getting it to execute correctly.

I downloaded the source for 1.3.0 and using checkinstall created a .deb package and installed it, but the necessary scripts are not part of the install.  An example initrc is included in the tar, but moving it to etc/X11/xinit to replace the current file and making it executable didn't work.

I then used aptitude and removed the XDM package, and attempted rebooting.  Startup would hang at executing local boot scripts.  I switched to another virtual console and executing SLiM directly, and it would display, but after entering my login and password, an error would occur, stating "slim could not execute login command" and then return to a blank prompt.

To get back to my usual setup I reinstalled the XDM package using Aptitude and ran it directly.

I know the issue stems from my lack of knowledge of scripting and which scripts are necessary, as other Login Managers set this up automatically.  Any ideas?

---

### Post by Stemp on 2007-09-26
I found something about Ubuntu & Slim but it's in Polish (I think) 
[http://uel.jogger.pl/2007/08/26/slim-alternatywny-menadzer-logowania/](http://uel.jogger.pl/2007/08/26/slim-alternatywny-menadzer-logowania/)

There is a link to a deb package (there is a real Ubuntu one in the gutsy repos).

---

### Post by kerry_s on 2007-09-26
you could just skip a log in manager all together and just use startx.

here's my script for auto starting x when you log in, put it at the bottom of .bash_profile

```

if [ `tty` = "/dev/tty1" ]; then
startx
fi

```

---

### Post by mojoman on 2007-09-26
I played around with slim a bit but I found it rather limited. I couldn't get the f1 alternative to work so I couldn't choose wm at login. It works ok on my laptop with Debian Etch where I got one user on one wm but I I recently set up a Debian Lenny partition on my desktop and here I got two users with different WM/DE and its limitation starts to show. However, to start whatever environment you want I think that the following is enough.

create a ~/.xinitrc and add on line in it, e.g.
```

exec icewm-session

```
```

exec xfce-session
```
```

exec fluxbox-session
```

If I want other stuff started I just add that in the file liked to the WM (e.g. ~/fluxbox/startup for fluxbox etc).

That worked for me but like I said, I found it a bit limiting on a system with multiple users or multiple WM/DE.

/mojoman

---

### Post by Antilles on 2007-09-28
First off, thanks for the help.

I've tried a lot of different things in the past couple days, so the order and exact content of these attempts may be slightly off.

Fumbling through the Polish (as well as a [French set of instructions]("http://wiki.archlinux.fr/howto:environnements_graphiques:xfce-slim") I found, though they're written for Arch Linux, and aren't entirely compatible) led to some progress, but it still isn't working right.  No matter how I try it, I end up with the console hanging at "Running local boot scripts (/etc/rc.local)".  At least I realized that one can just hit enter and log in to the shell instead of switching to another virtual console to do so, but that defeats the purpose of having a login manager.  

As I'm only running Xfce currently, I edited .xinitrc just to read "exec startxfce4", and if I run SLiM now, I no longer receive the "could not execute login command" error, and X comes up, so at least one issue has been solved.

As I assume the Polish is instructing, I set the runtimes of SLiM to 2,3,4,5 and set XDM to none using sysv-rc-conf, but I can't tell if this has had an effect or not.

I thought I had it when I found the update-rc.d command, and used it with the slim.sh file in /etc/init.d, and the output resembled the output when xdm is setup, but in the end, it didn't work either. 

[quote=mojoman]I couldn't get the f1 alternative to work so I couldn't choose wm at login. It works ok on my laptop with Debian Etch where I got one user on one wm but I I recently set up a Debian Lenny partition on my desktop and here I got two users with different WM/DE and its limitation starts to show.[/quote]
I don't run any window manager or desktop environment other than Xfce so that limitation isn't an issue (at least, for now), so how exactly did you get it to run in the first place?  Was it running as part of your startup?

---

### Post by mojoman on 2007-09-29
> **Antilles said:**
> First off, thanks for the help.

I've tried a lot of different things in the past couple days, so the order and exact content of these attempts may be slightly off.

Fumbling through the Polish (as well as a [French set of instructions]("http://wiki.archlinux.fr/howto:environnements_graphiques:xfce-slim") I found, though they're written for Arch Linux, and aren't entirely compatible) led to some progress, but it still isn't working right.  No matter how I try it, I end up with the console hanging at "Running local boot scripts (/etc/rc.local)".  At least I realized that one can just hit enter and log in to the shell instead of switching to another virtual console to do so, but that defeats the purpose of having a login manager.  

As I'm only running Xfce currently, I edited .xinitrc just to read "exec startxfce4", and if I run SLiM now, I no longer receive the "could not execute login command" error, and X comes up, so at least one issue has been solved.

As I assume the Polish is instructing, I set the runtimes of SLiM to 2,3,4,5 and set XDM to none using sysv-rc-conf, but I can't tell if this has had an effect or not.

I thought I had it when I found the update-rc.d command, and used it with the slim.sh file in /etc/init.d, and the output resembled the output when xdm is setup, but in the end, it didn't work either. 


I don't run any window manager or desktop environment other than Xfce so that limitation isn't an issue (at least, for now), so how exactly did you get it to run in the first place?  Was it running as part of your startup?

Slim itself starts out of the box for me but mind you, I'm using it on Debian Lenny and Etch. The only problem I had to deal with was getting slim to start the right graphical environment and for that, I just had to edit.xinitrc. If you ned to look at the cotent of any of my files, lett me know.

---

### Post by Antilles on 2007-09-29
If you could post the content of your slim.conf and the slim.sh file in /etc/init.d (if it exists) that would be helpful.

I'm beginning to think I should wait until Gutsy is released, and try getting this working then, as SLiM will be in the repositories. I hope that like on your Debian setups, installing from that package will work by default.

---

### Post by bonzodog on 2007-09-29
Antilles - You might want to think about maybe trying out Zenwalk Linux on your machine. It's the Xfce Poster Child distro, is *very* light, and uses SLiM as the default login manager as of 4.8 (which is still in Beta). 

Zenwalk is based on Slackware, and has it's own package manager. It's much faster than Ubuntu/Xubuntu.

---

### Post by mojoman on 2007-10-01
> **Antilles said:**
> If you could post the content of your slim.conf and the slim.sh file in /etc/init.d (if it exists) that would be helpful.

I'm beginning to think I should wait until Gutsy is released, and try getting this working then, as SLiM will be in the repositories. I hope that like on your Debian setups, installing from that package will work by default.


/etc/slim.conf

```
# Path, X server and arguments (if needed)
# Note: -xauth $authfile is automatically appended
default_path        ./:/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin
default_xserver     /usr/X11R6/bin/X
xserver_arguments   -dpi 100 -nolisten tcp

# Commands for halt, login, etc.
halt_cmd            /sbin/shutdown -h now
reboot_cmd          /sbin/shutdown -r now
console_cmd         /usr/X11R6/bin/xterm -C -fg white -bg black +sb -T "Console login" -e /bin/sh -c "/bin/cat /etc/issue; exec /bin/login"
#suspend_cmd        /usr/sbin/suspend

# Full path to the xauth binary
xauth_path         /usr/X11R6/bin/xauth 

# Xauth file for server
authfile           /var/run/slim.auth

# Activate numlock when slim starts. Valid values: on|off
numlock             on

# Hide the mouse cursor (note: does not work with some WMs).
# Valid values: true|false
# hidecursor          false

# This command is executed after a succesful login.
# you can place the %session and %theme variables
# to handle launching of specific commands in .xinitrc
# depending of chosen session and slim theme
#
# NOTE: if your system does not have bash you need
# to adjust the command according to your preferred shell,
# i.e. for freebsd use:
# login_cmd           exec /bin/sh - ~/.xsession %session
# login_cmd           exec /bin/bash -login /etc/X11/Xsession %session # commented
login_cmd           exec /bin/bash -login ~/.xinitrc %session
# Commands executed when starting and exiting a session.
# They can be used for registering a X11 session with
# sessreg. You can use the %user variable
#
# sessionstart_cmd	some command
# sessionstop_cmd	some command

# Start in daemon mode. Valid values: yes | no
# Note that this can overridden by the command line
# option "-d"
# daemon	yes

# Available sessions (first one is the default).
# The current chosen session name is replaced in the login_cmd
# above, so your login command can handle different sessions.
# see the xinitrc.sample file shipped with slim sources
sessions            xfce4-session,fluxbox,icewm,openbox,wmaker,blackbox

# Executed when pressing F11 (requires imagemagick)
screenshot_cmd      scrot /tmp/slim.png

# welcome message. Available variables: %host, %domain
welcome_msg         Welcome to %host

# shutdown / reboot messages
shutdown_msg       The system is halting...
reboot_msg         The system is rebooting...

# default user, leave blank or remove this line
# for avoid pre-loading the username.
#default_user        simone

# current theme, use comma separated list to specify a set to 
# randomly choose from
current_theme       debian-moreblue

# Lock file
lockfile            /var/run/slim.lock

# Log file
logfile             /var/log/slim.log
```

/etc/init.d/slim

```

#!/bin/sh

# Largely adapted from xdm's init script:
# Copyright 1998-2002, 2004, 2005 Branden Robinson <branden@debian.org>.
# Copyright 2006 Eugene Konev <ejka@imfi.kspu.ru>

### BEGIN INIT INFO
# Provides:          slim
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Should-Start:      xfs $named slapd
# Should-Stop:       xfs $named slapd
# Default-Start:     2 3 4 5
# Default-Stop:      S 0 1 6
# Short-Description: Start/stop the SLiM daemon.
### END INIT INFO

test -z "$HEED_DEFAULT_DISPLAY_MANAGER" && HEED_DEFAULT_DISPLAY_MANAGER=true
DEFAULT_DISPLAY_MANAGER_FILE=/etc/X11/default-display-manager

DAEMON=/usr/bin/slim
PIDFILE=/var/run/slim.lock

SSD_START_ARGS="--pidfile $PIDFILE --name $(basename $DAEMON) --startas $DAEMON -- -d"
SSD_STOP_ARGS="--pidfile $PIDFILE --name $(basename $DAEMON) --retry TERM/5/TERM/5"

case $1 in
  start)
    if [ "$HEED_DEFAULT_DISPLAY_MANAGER" = "true" ] &&
       [ -e $DEFAULT_DISPLAY_MANAGER_FILE ] &&
       [ "$(cat $DEFAULT_DISPLAY_MANAGER_FILE)" != "$DAEMON" ]; then
      echo "Not starting X display manager (slim); it is not the default display manager."
    else
      echo -n "Starting X display manager: slim"
      start-stop-daemon --start --quiet $SSD_START_ARGS || echo -n " already running"
      echo "."
    fi
  ;;

  stop)
    echo -n "Stopping X display manager: slim"
    if ! [ -f $PIDFILE ]; then
      echo -n " not running ($PIDFILE not found)"
    else
      start-stop-daemon --stop --quiet $SSD_STOP_ARGS
      SSD_RES=$?
      if [ $SSD_RES -eq 1 ]; then
        echo -n " not running"
      fi
      if [ $SSD_RES -eq 2 ]; then
        echo -n " not responding to TERM signals"
      else
    if [ -f $PIDFILE ]; then
      echo -n " (removing stale $PIDFILE)"
      rm $PIDFILE
    fi
      fi
    fi
    echo "."
  ;;

  restart)
    $0 stop
    sleep 2
    $0 start
  ;;

  force-reload)
    /etc/init.d/slim restart
  ;;

  *)
    echo "Usage: /etc/init.d/slim {start|stop|restart|force-reload}"
    exit 1
  ;;
esac

# End of file

```

Installing it from the repositories got it working right away for me. I had some serious problems setting it up for Etch (it's not in the repos for etch) and I ended up going back to a cli login. However, after I installed Lenny on my desktop (which has it in the repos) I gave it another go on my laptop and using the Lenny install as a map I got it working.

Hope this helps you out. 
/mojoman

---

### Post by eriqjaffe on 2008-02-16
Kinda hate to dig up an old thread, but...

I got SLiM working using the files in mojoman's post above (with a couple of minor tweaks), but the bit depth seems kinda screwy - my laptop can't handle being set to a 24-bit display properly, so I have my xorg.conf set to 16-bit which works fine.

However, the SLiM screen looks a litte off - you can kind of see how the gradients in the wallpaper aren't particularly smooth.  For reference, I'm adding a shot of my regular desktop on the right so you can really see the difference.  It's the exact same .PNG file, so I  don't think it's anything inherent in the image itself.

[[IMG]http://img255.imageshack.us/img255/6462/slimwf0.th.png[/IMG]](http://img255.imageshack.us/my.php?image=slimwf0.png)[[IMG]http://img516.imageshack.us/img516/3527/desktopscreenshot200802so1.th.png[/IMG]](http://img516.imageshack.us/my.php?image=desktopscreenshot200802so1.png)

...which is how the desktop (with the same background) looks when I set it to 24-bit.  I tried adding "-depth 16" to the xserver_arguments (which I think is a valid argument), but that doesn't seem to make a difference - is there anything I can do to force this?

---

### Post by cardinals_fan on 2008-02-16
I have only just installed slim - haven't even tried it yet.  Just wanted to say that you've got an awesome desktop there :)

---

