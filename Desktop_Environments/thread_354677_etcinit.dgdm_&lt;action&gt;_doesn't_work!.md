---
title: "/etc/init.d/gdm &lt;action&gt; doesn't work!"
date: 2007-02-06
forum: Desktop Environments
---

### Post by suhaib on 2007-02-06
When I typed the command, [FONT="Courier New"]/etc/init.d/gdm <action>[/FONT] I receive the error message, "No such file or directory".  To resolve this I have tried to reinstall gdm which hasn't made any noticeable changes.  When I boot up I have to log in via text-mode and type the command [FONT="Courier New"]startx [/FONT]to get some GUI.  I also tried the command [FONT="Courier New"]update-rc.d[/FONT] but I am ignorant of it's usage, I believe I'm missing some information in the last command.  All help is appreciated.

---

### Post by taurus on 2007-02-06
You mean these won't work at all!

```
sudo aptitude update
sudo aptitude install gdm
sudo /etc/init.d/gdm start
```

---

### Post by suhaib on 2007-02-06
> **taurus said:**
> You mean these won't work at all!

```
sudo aptitude update
sudo aptitude install gdm
sudo /etc/init.d/gdm start
```

The third doesn't work, no.  The former two are fine.  Although when I do run the reinstallation, I can't run the third.

---

### Post by taurus on 2007-02-06
```
ls -la /etc/init.d
```

---

### Post by suhaib on 2007-02-06
> **taurus said:**
> ```
ls -la /etc/init.d
```

Sadly there is no file or dir entitled "gdm".

---

### Post by taurus on 2007-02-06
Are you running Dapper or Edgy?  What if you run this command again?

```
sudo aptitude install ubuntu-desktop
```
and
```
locate gdm
```

---

### Post by suhaib on 2007-02-06
Sorry, I thought my profile displayed my version.  I'm running Edgy.  When I do aptitude commands, sometimes it works, and other times it shows its usage, closing with the message, "This aptitude does not have Super Cow Powers".

locate gdm produces a massive output of dirs and files.

---

### Post by taurus on 2007-02-06
How about 

```
sudo aptitude install ubuntu-desktop
whereis gdm
```

---

### Post by suhaib on 2007-02-06
Strangely, aptitude worked this time round.  After typing whereis gdm I got the following output,

[FONT="Courier New"]gdm: /usr/sbin/gdm /etc/gdm /usr/lib/gdm /usr/share/gdm /usr/share/man/man1/gdm.1.gz[/FONT]

---

### Post by taurus on 2007-02-06
And you don't have gdm in /etc/init.d?  If not, here is a copy of it so open a editor

```
gksudo gedit /etc/init.d/gdm
```
and save these in there.

```

#! /bin/sh
#
# Originally based on:
# Version:      @(#)skeleton  1.8  03-Mar-1998  miquels@cistron.nl
#
# Modified for gdm, Steve Haslam <steve@arise.dmeon.co.uk> 14mar99
# modified to remove --exec, as it does not work on upgrades. 18jan2000
# modified to use --name, to detect stale PID files 18mar2000
# sleep until gdm dies, then restart it 16jul2000
# get along with other display managers (Branden Robinson, Ryan Murray) 05sep200
1

set -e

# To start gdm even if it is not the default display manager, change
# HEED_DEFAULT_DISPLAY_MANAGER to "false."
HEED_DEFAULT_DISPLAY_MANAGER=true
DEFAULT_DISPLAY_MANAGER_FILE=/etc/X11/default-display-manager
PATH=/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/gdm
PIDFILE=/var/run/gdm.pid
UPGRADEFILE=/var/run/gdm.upgrade

if [ -e $UPGRADEFILE -a "$1" != "restart" -a "$1" != "force-reload" ]; then
        SSD_ARG="--startas $DAEMON"
        rm -f $UPGRADEFILE
else
        SSD_ARG="--exec $DAEMON"
fi

# Allow cdd to override the config
if [ -f /etc/gdm/gdm-cdd.conf ]; then
        CONFIG_FILE="--config=/etc/gdm/gdm-cdd.conf"
fi

test -x $DAEMON || exit 0

if [ -r /etc/environment ]; then
  if LANG=$(pam_getenv -l LANG); then
    export LANG
  fi
  if LANGUAGE=$(pam_getenv -l LANGUAGE); then
    export LANGUAGE
  fi

fi

. /lib/lsb/init-functions

case "$1" in
  start)
        if [ -e "$DEFAULT_DISPLAY_MANAGER_FILE" -a "$HEED_DEFAULT_DISPLAY_MANAGER" = "true" -a "$(cat $DEFAULT_DISPLAY_MANAGER_FILE 2>/dev/null)" != "$DAEMON" ]
; then
                log_warning_msg "Not starting GNOME Display Manager (gdm); it is not the default display manager."
        else
                # if usplash is runing, make sure to stop it now, yes "start" kills it.
                if pidof usplash > /dev/null; then
                        DO_NOT_SWITCH_VT=yes /etc/init.d/usplash start
                fi
                log_begin_msg "Starting GNOME Display Manager..."
                start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE -- name gdm $SSD_ARG -- $CONFIG_FILE >/dev/null 2>&1 || log_end_msg 1
                log_end_msg 0
        fi
  ;;
  stop)
        log_begin_msg "Stopping GNOME Display Manager..."
        start-stop-daemon --stop  --quiet --oknodo --pidfile $PIDFILE --name gdm $SSD_ARG --retry 30 >/dev/null 2>&1
        log_end_msg 0
  ;;
  reload)
        log_begin_msg "Reloading GNOME Display Manager configuration..."
        log_warning_msg "Changes will take effect when all current X sessions have ended."
        start-stop-daemon --stop --signal USR1 --quiet --pidfile \
                $PIDFILE --name gdm $SSD_ARG >/dev/null 2>&1
        log_end_msg 0
  ;;
  restart|force-reload)
        $0 stop || true
        $0 start
  ;;
  *)
        log_success_msg "Usage: /etc/init.d/gdm {start|stop|restart|reload|force-reload}"
        exit 1
  ;;
esac

exit 0

```
Now, change the permission to executable and launch it.

```
sudo chmod 755 /etc/init.d/gdm
sudo /etc/init.d/gdm start
```

---

### Post by suhaib on 2007-02-06
I get an error when I try to start it.  The error displays 53: Syntax error: ";" unexpected.

I'm assuming it's to do with line 53 of the gdm file?

---

### Post by taurus on 2007-02-06
Yes, it's the /etc/init.d/gdm.  Probably the cut 'n paste thing.  May need to move the ; from line 52 to the end of previous line (line 52) then.

---

### Post by suhaib on 2007-02-06
ok thanks I'll give that a shot.

---

### Post by suhaib on 2007-02-06
Ok after getting rid of all the pasting errors, such as characters being on new lines, starting didn't work, it fails, however the stopping gdm is successful.  Yet again, thanks for your support.

---

### Post by taurus on 2007-02-06
What happens if you reboot?

---

### Post by suhaib on 2007-02-06
The problem persists even after a reboot.

---

### Post by suhaib on 2007-02-09
Bump!!!

---

