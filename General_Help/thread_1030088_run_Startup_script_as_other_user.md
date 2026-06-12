---
title: "run Startup script as other user"
date: 2009-01-04
forum: General Help
---

### Post by Mandarine on 2009-01-04
Hello,

I would like to start TwonkyMediaServer my server. I have installed the program as described in the HOWTO and created  corresponding links in / etc/rc2.d and / etc/rc0.d. It will use the following script: 

```

#!/bin/sh
#
# MediaServer Control File written by Itzchak Rehberg
# Modified for fedora/redhat by Landon Bradshaw <phazeforward@gmail.com>
# Adapted to TwonkyMedia 3.0 by TwonkyVision GmbH
# Adapted to TwonkyMedia 4.0 by TwonkyVision GmbH
# Adapted to TwonkyMedia 5.0 by PacketVideo
#
# This script is intended for SuSE and Fedora systems.
#
#
###############################################################################
#
### BEGIN INIT INFO
# Provides:       twonkyserver
# Required-Start: $network $remote_fs
# Default-Start:  3 5
# Default-Stop:   0 1 2 6
# Description:    TwonkyMedia UPnP server
### END INIT INFO
#
# Comments to support chkconfig on RedHat/Fedora Linux
# chkconfig: 345 71 29
# description: TwonkyMedia UPnP server
#
#==================================================================[ Setup ]===

WORKDIR1="/usr/local/twonkymedia"
WORKDIR2="`dirname $0`"
PIDFILE=/var/run/mediaserver.pid

#=================================================================[ Script ]===

# Source function library.
if [ -f /etc/rc.status ]; then
  # SUSE
  . /etc/rc.status
  rc_reset
else
  # Reset commands if not available
  rc_status() {
    case "$1" in
	-v)
	    true
	    ;;
	*)
	    false
	    ;;
    esac
    echo
  }
  alias rc_exit=exit
fi


if [ -x "$WORKDIR1" ]; then
WORKDIR="$WORKDIR1"
else
WORKDIR="$WORKDIR2"
fi

DAEMON=twonkymedia
TWONKYSRV="${WORKDIR}/${DAEMON}"

cd $WORKDIR

case "$1" in
  start)
    if [ -e $PIDFILE ]; then
      PID=`cat $PIDFILE`
      echo "TwonkyMedia server seems already be running under PID $PID"
      echo "(PID file $PIDFILE already exists). Checking for process..."
      running=`ps --no-headers -o "%c" -p $PID`
      if ( [ "${DAEMON}"=="${running}" ] ); then
        echo "Process IS running. Not started again."
      else
        echo "Looks like the daemon crashed: the PID does not match the daemon."
        echo "Removing flag file..."
        rm $PIDFILE
        $0 start
        exit $?
      fi
      exit 0
    else
      if [ ! -x "${TWONKYSRV}" ]; then
	  echo "TwonkyMedia server not found".
	  rc_status -u
	  exit $?
      fi
      echo -n "Starting $TWONKYSRV ... "
      "$TWONKYSRV" -D
      rc_status -v
    fi
  ;;
  stop)
    if [ ! -e $PIDFILE ]; then
      echo "PID file $PIDFILE not found, stopping server anyway..."
      killall -s TERM twonkymedia
      rc_status -u
      exit 3
    else
      echo -n "Stopping Twonky MediaServer ... "
      PID=`cat $PIDFILE`
      kill -s TERM $PID
      rm -f $PIDFILE
      rc_status -v
    fi
  ;;
  reload)
    if [ ! -e $PIDFILE ]; then
      echo "PID file $PIDFILE not found, stopping server anyway..."
      killall -s TERM twonkymedia
      rc_status -u
      exit 3
    else
      echo -n "Reloading Twonky server ... "
      PID=`cat $PIDFILE`
      kill -s HUP $PID
      rc_status -v
    fi
  ;;
  restart)
    $0 stop
    $0 start
  ;;
  status)
    if [ ! -e $PIDFILE ]; then
      running="`ps ax --no-headers | grep -e twonkymedia | grep -v grep | grep -v twonkymedia.sh | cut -d ' ' -f 1`"
      if [ "${running}" == "" ]; then
        echo "No TwonkyMedia server is running"
      else
        echo "A TwonkyMedia server seems to be running with PID ${running}, but no PID file exists."
        echo "Probably no write permission for ${PIDFILE}."
      fi
      exit 0
    fi
    PID=`cat $PIDFILE`
    running=`ps --no-headers -o "%c" -p $PID`
    if ( [ "${DAEMON}"=="${running}" ] ); then
      echo "TwonkyMedia server IS running."
    else
      echo "Looks like the daemon crashed: the PID does not match the daemon."
    fi
  ;;
  *)
    echo ""
    echo "TwonkyMedia server"
    echo "------------------"
    echo "Syntax:"
    echo "  $0 {start|stop|restart|reload|status}"
    echo ""
    exit 3
  ;;
esac

rc_exit
```

The server launches and is accessible via Web interface. What bothers me only: The server runs as user "root". Can I somehow change that? I would like the script as a normal user (let's call him: twonky) ...

How does that work?

Sascha

---

### Post by jpkotta on 2009-01-05
You can run programs as another user with ```
su *user* -c *command*
```

At a minimum, you'll have to replace 
```
"$TWONKYSRV" -D
```
with
```
su twonky -c "$TWONKYSRV -D"
```

---

