---
title: "help,how to start tftp server?"
date: 2006-04-29
forum: Desktop Environments
---

### Post by lihlcnkr on 2006-04-29
hello all.
i'am newbee.
i will start tftftp server,bug i cant stat it.

i'ma installed atftpd,
and created /tftpboot directory, and set it can read and write.
and in server-admin start the atftpd server.

but tftp server is not started.
no message in ""netstat -a | grep tftp"

who can help me?
thx


sorry,my english is so poor.

ps: this is my tftpd config file
--------------------
fiel  /etc/xinetd.d/tftp
----------------------
service tftp
{
    protocol        = udp
    port            = 69
    socket_type     = dgram
    wait            = yes  
    user            = nobody
    group           = nobody
    server          = /usr/sbin/in.tftpd
    server_args     = /tftpboot         
    only_from       = 10.0.1.0 
    disable         = no      
}                       


----------------------

file  etc/init.d/atftpd  
----------------------
#! /bin/sh
#
# atftpd - Script to launch atftpd server. Based on Skeleton.
#

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/atftpd
NAME=atftpd
DESC="Advanced Trivial FTP server"
USE_INETD=true
OPTIONS=""

test -f $DAEMON || exit 0

set -e

if [ -f /etc/default/atftpd ]; then
    . /etc/default/atftpd
fi

if [ "$USE_INETD" = "true" ]; then
    exit 0;
fi

case "$1" in
  start)
	echo -n "Starting $DESC: "
	start-stop-daemon --start --oknodo --quiet --exec $DAEMON -- $OPTIONS
	echo "$NAME."
	;;
  stop)
	echo -n "Stopping $DESC: "
	start-stop-daemon --stop --oknodo --quiet --exec $DAEMON
	echo "$NAME."
	;;
  restart|reload|force-reload)
	echo -n "Restarting $DESC: "
	start-stop-daemon --stop --oknodo --quiet --exec $DAEMON
	sleep 1
	start-stop-daemon --start --oknodo --quiet --exec $DAEMON -- $OPTIONS
	echo "$NAME."
	;;
  *)
	N=/etc/init.d/$NAME
        echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
	exit 1
	;;
esac

exit 0

---

### Post by Jose Catre-Vandis on 2006-09-02
This thread might help
[http://www.ubuntuforums.org/showthread.php?t=148027&highlight=tftpd+start](http://www.ubuntuforums.org/showthread.php?t=148027&highlight=tftpd+start)

---

