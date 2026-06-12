---
title: "GDM problem in maverick"
date: 2011-08-18
forum: Desktop Environments
---

### Post by garvinrick4 on 2011-08-18
Have one install of Maverick that does not get much use and have noticed today
that it does not boot without going into a tty and restarting GDM. Is running just
have to stop and start then completes boot into X. Google searched and did not seem to
come with a answer.

---

### Post by garvinrick4 on 2011-08-18
rick@rick-laptop:~$ sudo update-rc.d -f gdm defaults
[COLOR=Red]update-rc.d: warning: /etc/init.d/gdm missing LSB information[/COLOR]  (below is script)
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/gdm ...
   /etc/rc0.d/K20gdm -> ../init.d/gdm
   /etc/rc1.d/K20gdm -> ../init.d/gdm
   /etc/rc6.d/K20gdm -> ../init.d/gdm
   /etc/rc2.d/S20gdm -> ../init.d/gdm
   /etc/rc3.d/S20gdm -> ../init.d/gdm
   /etc/rc4.d/S20gdm -> ../init.d/gdm
   /etc/rc5.d/S20gdm -> ../init.d/gdm


```
#!/bin/sh -e
# upstart-job
#
# [COLOR=Red]Symlink target for initscripts that have been converted to Upstart.
[/COLOR] 
set -e

INITSCRIPT="$(basename "$0")"
JOB="${INITSCRIPT%.sh}"

if [ "$JOB" = "upstart-job" ]; then
    if [ -z "$1" ]; then
        echo "Usage: upstart-job JOB COMMAND" 1>&2
    exit 1
    fi

    JOB="$1"
    INITSCRIPT="$1"
    shift
else
    if [ -z "$1" ]; then
        echo "Usage: $0 COMMAND" 1>&2
    exit 1
    fi
fi

COMMAND="$1"
shift


if [ -z "$DPKG_MAINTSCRIPT_PACKAGE" ]; then
    ECHO=echo
else
    ECHO=:
fi

$ECHO "Rather than invoking init scripts through /etc/init.d, use the service(8)"
$ECHO "utility, e.g. service $INITSCRIPT $COMMAND"

case $COMMAND in
status)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the $COMMAND(8) utility, e.g. $COMMAND $JOB"
    $COMMAND "$JOB"
    ;;
start|stop|restart)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the $COMMAND(8) utility, e.g. $COMMAND $JOB"
    PID=$(status "$JOB" 2>/dev/null | awk '/[0-9]$/ { print $NF }')
    if [ -z "$PID" ] && [ "$COMMAND" = "stop" ]; then
        exit 0
    elif [ -n "$PID" ] && [ "$COMMAND" = "start" ]; then
        exit 0
    elif [ -z "$PID" ] && [ "$COMMAND" = "restart" ]; then
        start "$JOB"
        exit 0
    fi
    $COMMAND "$JOB"
    ;;
reload|force-reload)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the reload(8) utility, e.g. reload $JOB"
    reload "$JOB"
    ;;
*)
    $ECHO
    $ECHO "The script you are attempting to invoke has been converted to an Upstart" 1>&2
    $ECHO "job, but $COMMAND is not supported for Upstart jobs." 1>&2
    exit 1
esac
```

---

### Post by garvinrick4 on 2011-08-19
I was looking for all these things that was and could be wrong with "gdm" turns out
that with Plymouth theme spinifity would just not let go and allow gdm to do its thing.

Choose another plymouth theme installed and updated-initramfs and good as new. 
#For new users choose a plymouth theme in Synaptics and install, as many as you desire then run below:
```
sudo update-alternatives --config default.plymouth 

```Will get a list of installed themes choose one by number then update-initramfs and new plymouth theme is in play.
```
sudo update-initramfs -u
```

---

