---
title: "Startup scripts"
date: 2009-04-27
forum: General Help
---

### Post by tenmilez on 2009-04-27
I'm running ubuntu server and I want to make it so that when I turn the machine on, without necessarily logging in, it turns on my subversion server. When I installed it it came without any kind of init.d script and so I found one and it doesn't seem to be working. I have no idea if it's being executed or how to tell if it is or what errors I might be getting. 

/etc/init.d/svnserve looks like this:
```

#!/bin/bash
#
#   /etc/rc.d/init.d/subversion
#
# Starts the Subversion Daemon
#
# chkconfig: 2345 90 10
# description: Subversion Daemon
# processname: svnserve
# pidfile: /var/lock/subsys/svnserve

source /etc/rc.d/init.d/functions

[ -x /usr/bin/svnserve ] || exit 1

### Default variables
SYSCONFIG="/srv/svn/svnconfig"

### Read configuration
[ -r "$SYSCONFIG" ] && source "$SYSCONFIG"

RETVAL=0
prog="svnserve"
desc="Subversion Daemon"
pidfile="/var/run/$prog.pid"

start() {
   echo -n $"Starting $desc ($prog): "
   daemon $prog -d $OPTIONS --pid-file $pidfile
   RETVAL=$?
   if [ $RETVAL -eq 0 ]; then
     touch /var/lock/subsys/$prog
   fi
   echo
}

obtainpid() {
   pidstr=`pgrep $prog`
   pidcount=`awk -v name="$pidstr" 'BEGIN{split(name,a," "); print length(a)}'`
   if [ ! -r "$pidfile" ] && [ $pidcount -ge 2 ]; then
        pid=`awk -v name="$pidstr" 'BEGIN{split(name,a," "); print a[1]}'`
        echo $prog is already running and it was not started by the init script.
   fi
}
stop() {
   echo -n $"Shutting down $desc ($prog): "
   if [ -r "$pidfile" ]; then
        pid=`cat $pidfile`
        kill -s 3 $pid
        RETVAL=$?
   else
        RETVAL=1
   fi
   [ $RETVAL -eq 0 ] && success || failure
   echo
   if [ $RETVAL -eq 0 ]; then
     rm -f /var/lock/subsys/$prog
     rm -f $pidfile
   fi
   return $RETVAL
}

restart() {
        stop
        start
}
forcestop() {
   echo -n $"Shutting down $desc ($prog): "

   kill -s 3 $pid
   RETVAL=$?
   [ $RETVAL -eq 0 ] && success || failure
   echo
   if [ $RETVAL -eq 0 ]; then
     rm -f /var/lock/subsys/$prog
     rm -f $pidfile
   fi

   return $RETVAL
}

status() {
   if [ -r "$pidfile" ]; then
        pid=`cat $pidfile`
   fi
   if [ $pid ]; then
           echo "$prog (pid $pid) is running..."
   else
        echo "$prog is stopped"
    fi
}

obtainpid

case "$1" in
  start)
   start
   ;;
  stop)
   stop
   ;;
  restart)
   restart
   RETVAL=$?
   ;;
  condrestart)
   [ -e /var/lock/subsys/$prog ] && restart
   RETVAL=$?
   ;;
  status)
   status
   ;;
       forcestop)
   forcestop
   ;;
  *)
   echo $"Usage: $0 {start|stop|forcestop|restart|condrestart|status}"
   RETVAL=1
esac

exit $RETVAL
                                                       

```

and /srv/svn/svnconfig looks like this:
```
#!/bin/bash
# options for svnserve loaded with the /etc/init.d script
OPTIONS="-r /srv/svn/"
```


When the machine is all done booting up snvserve isn't running at all. 

Can anyone point me in the right direction? Thank you.


Edit: Replaced script with the one found here [http://www.section6.net/wiki/index.php/Setting_up_Subversion_in_Linux](http://www.section6.net/wiki/index.php/Setting_up_Subversion_in_Linux) and removed the referenced one.

---

### Post by kerry_s on 2009-04-27
have you tried just putting "svnserve &" in /etc/rc.local?

---

