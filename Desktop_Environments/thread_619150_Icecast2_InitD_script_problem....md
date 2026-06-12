---
title: "Icecast2 InitD script problem..."
date: 2007-11-21
forum: Desktop Environments
---

### Post by fatmcgav on 2007-11-21
Hi there,

I'm trying to run icecast v2.3.1 on Ubuntu Gutsy with mpd.

When i try to start icecast via the init.d script, it gives me the following error:
> 
Starting Icecast2: start-stop-daemon: Unable to set GID to 120 (Operation not permitted)

I'll post up the contents of the icecast2 init.d script next, but i've checked /etc/group and /etc/passwd and they are all valid...

Any ideas people???

Here's the init.d script...
```

#! /bin/sh
#
# icecast2
#
#      Written by Miquel van Smoorenburg <miquels@cistron.nl>.
#      Modified for Debian
#      by Ian Murdock <imurdock@gnu.ai.mit.edu>.
#
#      Further modified by Keegan Quinn <ice@thebasement.org>
#      for use with Icecast 2
#

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/bin/icecast2
NAME=icecast2
DESC=icecast2

test -x $DAEMON || exit 0

# Defaults
CONFIGFILE="/etc/icecast2/icecast.xml"
CONFIGDEFAULTFILE="/etc/default/icecast2"
USERID=icecast2
GROUPID=icecast
ENABLE="false"

# Reads config file (will override defaults above)
[ -r "$CONFIGDEFAULTFILE" ] && . $CONFIGDEFAULTFILE

if [ "$ENABLE" != "true" ]; then
   echo "$NAME daemon disabled - read $CONFIGDEFAULTFILE."
   exit 0
fi

set -e

case "$1" in
  start)
   echo -n "Starting $DESC: "
   start-stop-daemon --start --quiet --chuid $USERID:$GROUPID \
      --exec $DAEMON -- -b -c $CONFIGFILE
   echo "$NAME."
   ;;
  stop)
   echo -n "Stopping $DESC: "
   start-stop-daemon --stop --oknodo --quiet --exec $DAEMON
   echo "$NAME."
   ;;
  reload|force-reload)
   echo "Reloading $DESC configuration files."
   start-stop-daemon --stop --signal 1 --quiet --exec $DAEMON
   ;;
  restart)
   echo -n "Restarting $DESC: "
   start-stop-daemon --stop --oknodo --quiet --exec $DAEMON
   sleep 1
   start-stop-daemon --start --quiet --chuid $USERID:$GROUPID \
      --exec $DAEMON -- -b -c $CONFIGFILE
   echo "$NAME."
   ;;
  *)
   echo "Usage: $0 {start|stop|restart|reload|force-reload}" >&2
   exit 1
   ;;
esac

exit 0
```


Cheers
Fatmcgav

---

