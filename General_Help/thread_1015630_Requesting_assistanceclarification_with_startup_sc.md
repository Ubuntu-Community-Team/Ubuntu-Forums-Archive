---
title: "Requesting assistance/clarification with startup scripts"
date: 2008-12-19
forum: General Help
---

### Post by rommyappus on 2008-12-19
Well, I'm switching my server from Slackware to Ubuntu and I'm finding there are a few major differences. The relevant one for me now is the init.d process.

In Slackware, rc.local was executed once when entering the final runlevel but it seems Ubuntu runs this several times (Every time the runlevel is changed.) 

I've read a very good article[describing Ubuntu's init.d process]("http://http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/") and I'm pretty confident I can make something that at least -works- but I'd like to be a bit more compliant with the runlevel syntax. For this exercise, I'm going to start a bittorrent tracker and (eventually) a client to seed a list of trackers. For now I'd like to focus on the tracker, because I can apply this knowledge to anything else I will do in the future (The client being one of them)

From what I've been able to find through google, there actually used to be a bittorrent tracker startup script - do any of you have it?

Otherwise, here is the preliminary startup script I've come up with .. have I made any big mistakes or oversights?

(This is based off of the samba startup script, btw)

#!/bin/sh

### BEGIN INIT INFO
# Provides:          Bittorrent tracker
# Required-Start:    $network $local_fs $remote_fs
# Required-Stop:     $network $local_fs $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Should-Start:      slapd
# Should-Stop:       slapd
# Short-Description: start Bittorrent tracker 
### END INIT INFO

TRACKER=/usr/bin/bttrack
PIDDIR=/var/run/bttrack
TRACKERPID=$PIDDIR/bttrack.pid
DLDRNFO=/var/bttrack.temp

# clear conflicting settings from the environment
unset TMPDIR

# See if the daemons are there
test -x /usr/bin/bttrack || exit 0

. /lib/lsb/init-functions

case "$1" in
	start)
		log_daemon_msg "Starting Bittorrent tracker"
		# Make sure we have our PIDDIR, even if it's on a tmpfs
		install -o root -g root -m 755 -d $PIDDIR


		log_progress_msg "bttrack"
		if ! start-stop-daemon --start --quiet --oknodo --exec /usr/bin/bttrack -- --dfile $dldrnfo; then
			log_end_msg 1
			exit 1
		fi

		log_end_msg 0
		;;
	stop)
		log_daemon_msg "Stopping Bittorrent tracker"
		log_progress_msg ""

		start-stop-daemon --stop --quiet --pidfile $TRACKERPID
		# Wait a little and remove stale PID file
		sleep 1
		if [ -f $TRACKERPID ] && ! ps h `cat $TRACKERPID` > /dev/null
		then
			# Stale PID file (bttrack was succesfully stopped),
			# remove it (should be removed by bttrack itself IMHO.)
			rm -f $TRACKERPID
		fi

		log_end_msg 0

		;;
	restart|force-reload)
		$0 stop
		sleep 1
		$0 start
		;;
	status)
		status="0"
		status_of_proc -p $TRACKERPID /usr/bin/bttrack bttrack || status=$?
		exit $status
		;;
	*)
		echo "Usage: /etc/init.d/bttrack {start|stop|restart|status}"
		exit 1
		;;
esac

exit 0

---

### Post by rommyappus on 2008-12-19
This seems to work ok except it isn't really passing an argument along with the startup.

The original line read something like
... /path/to/executable -- -D However bttrack uses --dfile which doesn't seem to be compatable.. and there's no single dash variant in the man page.

---

### Post by rommyappus on 2008-12-19
Well - for now I'm just gonna toss it into rc.local ...

---

### Post by rommyappus on 2008-12-19
Bump for assistance today.
I believe my script works but I cannot find a way to pass an argument that uses two dashes with the start-stop-daemon

---

### Post by animacide on 2011-01-07
Hey Rommyappus,

To get this to work all you need to do is enclose the arguments in quotes like so:

```
if ! start-stop-daemon --start --quiet --oknodo --exec /usr/bin/bttrack -- "--dfile $dldrnfo"; then
```

However, to make it easier to tweak, I recommend using a variable for the arguments:

```
#!/bin/sh

### BEGIN INIT INFO
# Provides: Bittorrent tracker
# Required-Start: $network $local_fs $remote_fs
# Required-Stop: $network $local_fs $remote_fs
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Should-Start: slapd
# Should-Stop: slapd
# Short-Description: start Bittorrent tracker
### END INIT INFO

TRACKER=/usr/bin/bttrack
PIDDIR=/var/run/bttrack
TRACKERPID=$PIDDIR/bttrack.pid
DLDRNFO=/var/bttrack.temp
[B]DAEMON_ARGS="--dfile $DLDRNFO"
DAEMON=/usr/bin/bttrack[/B]

# clear conflicting settings from the environment
unset TMPDIR

# See if the daemons are there
test -x **$DAEMON** || exit 0

. /lib/lsb/init-functions

case "$1" in
start)
log_daemon_msg "Starting Bittorrent tracker"
# Make sure we have our PIDDIR, even if it's on a tmpfs
install -o root -g root -m 755 -d $PIDDIR


log_progress_msg "bttrack"
if ! start-stop-daemon --start --quiet --oknodo --exec **$DAEMON** -- **$DAEMON_ARGS**; then
log_end_msg 1
exit 1
fi

log_end_msg 0
;;
stop)
log_daemon_msg "Stopping Bittorrent tracker"
log_progress_msg ""

start-stop-daemon --stop --quiet --pidfile $TRACKERPID
# Wait a little and remove stale PID file
sleep 1
if [ -f $TRACKERPID ] && ! ps h `cat $TRACKERPID` > /dev/null
then
# Stale PID file (bttrack was succesfully stopped),
# remove it (should be removed by bttrack itself IMHO.)
rm -f $TRACKERPID
fi

log_end_msg 0

;;
restart|force-reload)
$0 stop
sleep 1
$0 start
;;
status)
status="0"
status_of_proc -p $TRACKERPID **$DAEMON** bttrack || status=$?
exit $status
;;
*)
echo "Usage: /etc/init.d/bttrack {start|stop|restart|status}"
exit 1
;;
esac

exit 0
```

---

