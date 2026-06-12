---
title: "Need a sudo'd process to run at boot"
date: 2009-02-04
forum: General Help
---

### Post by Kain000 on 2009-02-04
Hello everyone,

I am setting up my box for media streaming and have come across a problem, the command to launch Ushare (the streaming app) is:
```
sudo /etc/init.d/ushare start
```

I need this command to run from boot time, I thought about using the built in deal with system>pref>sessions    the only problem is that it requires the use of sudo.  

I tried a shell script
```
#!bin/bash
sleep 10
sudo /etc/init.d/ushare start
```
but I run into the same problem.

Now I could have the system auto loginto root, but that would be dangerous.
Idealy I just want the command itself to run either without using sudo or using sudo without needing a password.

any help?

thanks everyone

---

### Post by Yashiro on 2009-02-04
Install from the repos and it does everything out of the box. No need to start it up manually.

If you want to do it manually, just put it into /etc/rc.local. 
(but there are problems with this method if you re-log without a reboot or another user logs in)

---

### Post by Kain000 on 2009-02-05
> **Yashiro said:**
> Install from the repos and it does everything out of the box. No need to start it up manually.

If you want to do it manually, just put it into /etc/rc.local.


It would be nice to use the repos verition, but I need this custom patched ver. to be used with a xbox360 and a ps3 (outlined here [http://ubuntuforums.org/showthread.php?t=848144](http://ubuntuforums.org/showthread.php?t=848144) )

So if I move the entire ushare folder into the /etc/rc.local folder and it would start on boot?

---

### Post by Yashiro on 2009-02-05
Your guide there tells you what to do already.

No. rc.local is a FILE, you edit it with the commands you want to run.

---

### Post by jocko on 2009-02-05
> **Kain000 said:**
> It would be nice to use the repos verition, but I need this custom patched ver. to be used with a xbox360 and a ps3 (outlined here [http://ubuntuforums.org/showthread.php?t=848144](http://ubuntuforums.org/showthread.php?t=848144) )

So if I move the entire ushare folder into the /etc/rc.local folder and it would start on boot?
/etc/rc.local is a text file where you can put commands that you want to run during boot.
In a terminal:```

gksudo gedit /etc/rc.local
```
Put your command (without sudo, as it will be run as root anyway) in the file and save it. That should be it.

---

### Post by Kain000 on 2009-02-05
> **jocko said:**
> /etc/rc.local is a text file where you can put commands that you want to run during boot.
In a terminal:```

gksudo gedit /etc/rc.local
```
Put your command (without sudo, as it will be run as root anyway) in the file and save it. That should be it.

alright thankyou guys for your help.

---

### Post by Yellow Pasque on 2009-02-05
DO NOT use rc.local for this.
Follow step 6 in the guide you linked to instead.

Using rc.local will start the daemon at boot, but won't stop it when changing runlevels.

---

### Post by Yashiro on 2009-02-05
Indeed but I think he's aware of this and it resolves some issue with the way they're going about it.

It would be better to use update rc.d, yes.

If you want to know what it actually does I fished this out for you, Kain. [http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)

---

### Post by Kain000 on 2009-02-05
> **Temüjin said:**
> DO NOT use rc.local for this.
Follow step 6 in the guide you linked to instead.

Using rc.local will start the daemon at boot, but won't stop it when changing runlevels.

Yes I tred this step:
```
sudo update-rc.d ushare defaults
```
however ushare still doent run at boot.  

I realize that using rc.local will cause problems with muti session machines, but this box is intended as a stand allone media server, that will not be logged out, and mostlikely wont even be powered down, 

it's for a friend who doesnt know anything about linux and I am trying to ease him into the ubuntu mindset by first solving his streaming issues with windows.  

I dotn undersdand why updating the default runlevel to include ushare doesnt work.

Perhaps because the command to run it is ```
sudo /etc/init.d/ushare **start** ?
```

Is it a sudo issue or mabye it's the qualifier "start" on the end that is messing it up?

---

### Post by Yashiro on 2009-02-05
You need to make sure the 'ushare' shell script is in /etc/init.d and is executable.

Here is the script from the version in the repos.
```

#!/bin/sh -e
#
# uShare init script
#
### BEGIN INIT INFO
# Provides:          ushare
# Required-Start:    $local_fs $syslog $network
# Should-Start:
# Required-Stop:
# Should-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: uShare
# Description:       uShare UPnP (TM) A/V & DLNA Media Server
#                    You should edit configuration in /etc/ushare.conf file
#                    See http://ushare.geexbox.org for details
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/bin/ushare
NAME=ushare
DESC="uShare UPnP A/V & DLNA Media Server"
PIDFILE=/var/run/ushare.pid
CONFIGFILE=/etc/ushare.conf

# abort if no executable exists
[ -x $DAEMON ] || exit 0

# Get lsb functions
. /lib/lsb/init-functions
. /etc/default/rcS

[ -f /etc/default/ushare ] && . /etc/default/ushare

checkpid() {
  [ -e $PIDFILE ] || touch $PIDFILE
}

check_shares() {
  if [ -r "$CONFIGFILE" ]; then
    . $CONFIGFILE
    [ -n "$USHARE_DIR" ] && return 0
  fi
  return 1
}

case "$1" in
  start)
    log_daemon_msg "Starting $DESC: $NAME"
    if ! $(check_shares); then
      log_warning_msg "No shares avalaible ..."
      log_end_msg 0
    else
      checkpid
      start-stop-daemon --start --quiet --background --oknodo \
        --make-pidfile --pidfile $PIDFILE \
        --exec $DAEMON -- $USHARE_OPTIONS
             #   --exec $DAEMON -- $USHARE_OPTIONS --xbox
      log_end_msg $?
    fi
  ;;
  stop)
    log_daemon_msg "Stopping $DESC: $NAME"
    start-stop-daemon --stop --signal 2 --quiet --oknodo --pidfile $PIDFILE
    log_end_msg $?
  ;;
  reload|force-reload)
    log_daemon_msg "Reloading $DESC: $NAME"
    start-stop-daemon --stop --signal 1 --quiet --oknodo --pidfile $PIDFILE --exec $DAEMON 
    log_end_msg $?
  ;;
  restart)
    $0 stop
    # start-stop-daemon --stop --signal 2 --quiet --oknodo --pidfile $PIDFILE
    $0 start
          start-stop-daemon --start --quiet --background --oknodo \
        --make-pidfile --pidfile $PIDFILE \
        --exec $DAEMON -- $USHARE_OPTIONS
  ;;
  *)
    N=/etc/init.d/$NAME
    log_success_msg "Usage: $N {start|stop|restart|reload|force-reload}"
    exit 1
  ;;
esac

exit 0

```

---

### Post by Kain000 on 2009-02-05
> **Yashiro said:**
> Indeed but I think he's aware of this and it resolves some issue with the way they're going about it.

It would be better to use update rc.d, yes.

If you want to know what it actually does I fished this out for you, Kain. [http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)

Thank you all for your help with this, 

and thank you Yashiro for the VERY helpful link.

Like you guys pointed out, as did the debian site, ushare script was in the right place but not executable, so I did a chmod 755.

---

