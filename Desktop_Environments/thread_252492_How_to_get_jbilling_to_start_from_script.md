---
title: "How to get jbilling to start from script?"
date: 2006-09-06
forum: Desktop Environments
---

### Post by dgermann on 2006-09-06
Hi--

I can get jbilling to start from the command line, but when I try to get it from a script, it does not start.

A friend who has a Debian system has helped me with the script, but it does not seem to start the application. There is a thread [here]("http://www.jbilling.com/?q=node/75") which shows everything we've tried.

To save you some clicking through time, here is what the script says:

```
#!/bin/bash
# /etc/init.d/jbilling: Start and stop jbilling
#
#
ECHO=/bin/echo
TEST=/usr/bin/test
#
#
#
JBOSS_START_SCRIPT="/home/doug/jbilling/bin/run.sh"
JBOSS_STOP_SCRIPT="/home/doug/jbilling/bin/shutdown.sh"

$TEST -x ${JBOSS_START_SCRIPT} || exit 0
$TEST -x ${JBOSS_STOP_SCRIPT} || exit 0

start() {
$ECHO -n "Starting JBoss"
su - doug -c "$JBOSS_START_SCRIPT -c jbilling > /dev/null 2> /dev/null &"
$ECHO "."
}

stop() {
$ECHO -n "Stopping JBoss"
su - doug -c "$JBOSS_STOP_SCRIPT -S > /dev/null &"
$ECHO "."
}

case "$1" in
start)
start
;;
stop)
stop
;;
restart)
stop
sleep 30
start
;;
*)
$ECHO "Usage: jboss {start|stop|restart}"
exit 1
esac

exit 0

```

When I run the script I get this:

```
root@doug2:/etc/init.d #  /etc/init.d/jbilling start
Starting JBoss.
root@doug2:/etc/init.d # ps aux |grep jbilling
root     19743  0.0  0.1   2876   800 pts/0    S+   21:56   0:00 grep jbilling
root@doug2:/etc/init.d #
```

Anybody have any ideas how to trouble shoot this?

Thanks!

---

