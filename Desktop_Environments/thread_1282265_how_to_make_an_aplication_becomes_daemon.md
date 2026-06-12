---
title: "how to make an aplication becomes daemon"
date: 2009-10-04
forum: Desktop Environments
---

### Post by skynet1986 on 2009-10-04
Sorry I am a newbie in linux. I have already made a console application using lazarus. Now I am going to make this console application become a daemon so that it can be started automatically when my system boots up. I have already edited /etc/init.d/skeleton but I am confused about the script and how to run my console application. Could someone give me an example? here is my init.d script.Thank you.


#! /bin/sh
### BEGIN INIT INFO
# Provides:          skeleton 
# Required-Start:    $remote_fs
# Required-Stop:     $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Example initscript
# Description:       This file should be used to construct scripts to be
#                    placed in /etc/init.d.
### END INIT INFO

# Author: Foo Bar <foobar@baz.org>
#
# Please remove the "Author" lines above and replace them
# with your own name if you copy and modify this script.

# Do NOT "set -e"

# PATH should only include /usr/* if it runs after the mountnfs.sh script
#PATH=/sbin:/usr/sbin:/bin:/usr/bin:/home/ubuntu/Daemons
PATH=/home/ubuntu/Daemons
BIN=/home/ubuntu/Daemons/cleandirs
DESC="Testing Daemos"
NAME=cleandirs
DAEMON=/usr/sbin/$NAME
DAEMON_ARGS="-r"
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Exit if the package is not installed
#[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
#[ -r /etc/default/$NAME ] && . /etc/default/$NAME

# Load the VERBOSE setting and other rcS variables
#. /lib/init/vars.sh

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

#
# Function that starts the daemon/service
#
do_start()
{
	# Return
	#   0 if daemon has been started
	#   1 if daemon was already running
	#   2 if daemon could not be started
	#start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON --test > /dev/null \
	#	|| return 1
	#start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON -- \
	#	$DAEMON_ARGS \
	#	|| return 2
	cleandirs -r
	# Add code here, if necessary, that waits for the process to be ready
	# to handle requests from services started subsequently which depend
	# on this one.  As a last resort, sleep for some time.
}

#
# Function that stops the daemon/service
#
do_stop()
{
	# Return
	#   0 if daemon has been stopped
	#   1 if daemon was already stopped
	#   2 if daemon could not be stopped
	#   other if a failure occurred
	start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
	RETVAL="$?"
	[ "$RETVAL" = 2 ] && return 2
	# Wait for children to finish too if this is a daemon that forks
	# and if the daemon is only ever run from this initscript.
	# If the above conditions are not satisfied then add some other code
	# that waits for the process to drop all resources that could be
	# needed by services started subsequently.  A last resort is to
	# sleep for some time.
	start-stop-daemon --stop --quiet --oknodo --retry=0/30/KILL/5 --exec $DAEMON
	[ "$?" = 2 ] && return 2
	# Many daemons don't delete their pidfiles when they exit.
	rm -f $PIDFILE
	return "$RETVAL"
}

#
# Function that sends a SIGHUP to the daemon/service
#
do_reload() {
	#
	# If the daemon can reload its configuration without
	# restarting (for example, when it is sent a SIGHUP),
	# then implement that here.
	#
	start-stop-daemon --stop --signal 1 --quiet --pidfile $PIDFILE --name $NAME
	return 0
}

case "$1" in
  start)
	[ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
	do_start
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  stop)
	[ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
	do_stop
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  #reload|force-reload)
	#
	# If do_reload() is not implemented then leave this commented out
	# and leave 'force-reload' as an alias for 'restart'.
	#
	#log_daemon_msg "Reloading $DESC" "$NAME"
	#do_reload
	#log_end_msg $?
	#;;
  restart|force-reload)
	#
	# If the "reload" option is implemented then remove the
	# 'force-reload' alias
	#
	log_daemon_msg "Restarting $DESC" "$NAME"
	do_stop
	case "$?" in
	  0|1)
		do_start
		case "$?" in
			0) log_end_msg 0 ;;
			1) log_end_msg 1 ;; # Old process is still running
			*) log_end_msg 1 ;; # Failed to start
		esac
		;;
	  *)
	  	# Failed to stop
		log_end_msg 1
		;;
	esac
	;;
  *)
	#echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
	echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
	exit 3
	;;
esac

:
PATH=/home/ubuntu/Daemons

---

### Post by Lars Noodén on 2009-10-04
> **skynet1986 said:**
> Sorry I am a newbie in linux. I have already made a console application using lazarus. Now I am going to make this console application become a daemon so that it can be started automatically when my system boots up. ...

@skynet1986 : you rock!  

AFIAK [lazarus](http://www.lazarus.freepascal.org/) is mostly for making gui desktop applications.  How are you using it for this task?
For the example, what is the full path of your application to be launched?

As far as the shell script goes, take it in smaller chunks.  Write several smaller studies as separate learning scripts.  Then start make newer, more complex scripts.  

Pieces:

[LIST]
[*]case / esac
[*]environment variables
[*]subroutines
[*]ARGV
[/LIST]

See:
[http://steve-parker.org/sh/sh.shtml](http://steve-parker.org/sh/sh.shtml)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

and of course, [bash(1)](http://linux.die.net/man/1/bash)

---

