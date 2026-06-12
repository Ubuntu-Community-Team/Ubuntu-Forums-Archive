---
title: "Server (no GUI) Mediatomb Init Script Issue"
date: 2009-03-27
forum: General Help
---

### Post by beese on 2009-03-27
I have been scratching my head with this one forever.  I have a ubuntu server feeding a PS3 with mediatomb and it works brilliantly, but I have to SSH in to start mediatomb everytime.  I have searched the internets high and low and found many other problems people have with this, but none seem to have this one.  I suspect it is a general issue with my understanding of linux.

I have tried different settings with two different versions of supplied scripts for init.d and always get the same error in the /var/log/mediatomb.log (or just /var/log/mediatomb with a modified init script I have):-

```
2009-03-27 23:17:31    INFO: Loading configuration from: /etc/mediatomb/config.xml
2009-03-27 23:17:31    INFO: Checking configuration...
2009-03-27 23:17:31    INFO: Setting filesystem import charset to UTF-8
2009-03-27 23:17:31    INFO: Setting metadata import charset to UTF-8
2009-03-27 23:17:31    INFO: Setting playlist charset to UTF-8
2009-03-27 23:17:31    INFO: Configuration check succeeded.
2009-03-27 23:17:31    INFO: Initialized port: 50500
2009-03-27 23:17:31    INFO: Server bound to: 192.168.0.1
2009-03-27 23:17:32   ERROR: writeBookmark: failed to open: /home/public/.mediatomb/mediatomb.html

```

My init script currently looks as follows:- 

```
#! /bin/sh 
#
# MediaTomb initscript
#
# Original Author: Tor Krill .
# Modified by:     Leonhard Wimmer 
#
#

### BEGIN INIT INFO
# Provides:          mediatomb
# Required-Start:    $all
# Required-Stop:     $all
# Should-Start:      $all
# Should-Stop:       $all
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: upnp media server
### END INIT INFO


set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="upnp media server"
NAME=mediatomb
DAEMON=/usr/bin/$NAME
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME
USER=mediatomb
GROUP=mediatomb
LOGFILE=/var/log/mediatomb
HOME=/user/public/mediatomb

# Read config file if it is present.
if [ -r /etc/default/$NAME ]
then
	. /etc/default/$NAME
fi

# if NO_START is set, exit gracefully
[ "$NO_START" = "yes" ] && exit 0

D_ARGS="-c /etc/mediatomb/config.xml -d -u $USER -g $GROUP -m $HOME -P $PIDFILE -l $LOGFILE"

if [ "$INTERFACE" != "" ] ; then
    D_ARGS="$D_ARGS -e $INTERFACE"
fi



# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

#
#       Function that starts the daemon/service.
#
d_start() {
	touch $PIDFILE
	chown $USER:$GROUP $PIDFILE
	touch $LOGFILE
	chown $USER:$GROUP $LOGFILE
        start-stop-daemon --start --quiet --pidfile $PIDFILE \
                --exec $DAEMON -- $D_ARGS $DAEMON_OPTS
}

#
#       Function that stops the daemon/service.
#
d_stop() {
        start-stop-daemon --stop --signal 2 --retry 5 --quiet --pidfile $PIDFILE \
                --name $NAME
        rm $PIDFILE
}

#
#       Function that sends a SIGHUP to the daemon/service.
#
d_reload() {
        start-stop-daemon --stop --quiet --pidfile $PIDFILE \
                --name $NAME --signal 1
}

case "$1" in
  start)
        echo -n "Starting $DESC: $NAME"
        if [ "$INTERFACE" != "" ] ; then
            # try to add the multicast route
            /sbin/route add -net 239.0.0.0 netmask 255.0.0.0 $INTERFACE  >/dev/null 2>&1 || true
	fi
        d_start
        echo "."
        ;;
  stop)
        echo -n "Stopping $DESC: $NAME"
        d_stop
        echo "."
        ;;
  reload|force-reload)
        echo -n "Reloading $DESC configuration..."
        d_reload
        echo "done."
  	;;
  restart)
        #
        #       If the "reload" option is implemented, move the "force-reload"
        #       option to the "reload" entry above. If not, "force-reload" is
        #       just the same as "restart".
        #
        echo -n "Restarting $DESC: $NAME"
        d_stop
        sleep 1
        d_start
        echo "."
        ;;
  *)
        # echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
        echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0
```


It is so frustrating that just running 'mediatomb -d' does what I want, but my lack of experience is stopping me from getting this to work on boot.  The mediatomb.html file is definately in the place it says it is looking, so I guess this is a runlevel/user issue?

Thanks in advance for help, let me know if you need more info...

---

### Post by wesg on 2009-05-02
I'm actually having the same problem. I compiled mediatomb from source, and I just can't get the system to work on boot. mediatomb -d does the job, but I don't want to do that the whole time. When I use the init script with the location of /usr/local/bin I get feedback from /etc/init.d/ that says fail but when I use the default /usr/bin, I get nothing. I'd really like to see what's going on.

---

### Post by fatdunky on 2010-05-23
I had this problem from the normal command line, sudo'ing it fixed the problem. Though i'd assume its running a root all ready for you

*update* yeah got the same problem when trying to auto boot mediatomb. I just chown'd and chmod 777 the file mentioned in the error and it solved the problem

---

