---
title: "How to increase ulimit (ie. for Tor server)"
date: 2009-04-29
forum: General Help
---

### Post by shoeheight on 2009-04-29
Hello all,

I have been having difficulty running my tor server due to regular Vidalia/Tor crashes.  The server runs fine for ~12hrs then crashes with an "increase the ulimit" error. 

Checking my ulimit  ```
$ ulimit -n
``` gives me a value of 1024. I would like to increase my ulimit to the guidelines given in the "tor.init" file I attached, which is a "conservative" 8192.

How can I force this change in my ulimit each time the system boots up? Should I place this file in a directory to make it run on startup or will it restart tor and cause an error with my current vidalia install?

Any help would be appreciated...especially if it solves the problem... :)

[PHP]#! /bin/bash

### BEGIN INIT INFO
# Provides:          tor
# Required-Start:    $local_fs $remote_fs $network $named $time
# Required-Stop:     $local_fs $remote_fs $network $named $time
# Should-Start:      $syslog
# Should-Stop:       $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Starts The Onion Router daemon processes
# Description:       Start The Onion Router, a TCP overlay
#                    network client that provides anonymous
#                    transport.
### END INIT INFO

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/tor
NAME=tor
DESC="tor daemon"
TORPIDDIR=/var/run/tor
TORPID=$TORPIDDIR/tor.pid
DEFAULTSFILE=/etc/default/$NAME
WAITFORDAEMON=60
ARGS=""
# Let's try to figure our some sane defaults:
if [ -r /proc/sys/fs/file-max ]; then
	system_max=`cat /proc/sys/fs/file-max`
	if [ "$system_max" -gt "80000" ] ; then
		MAX_FILEDESCRIPTORS=32768
	elif [ "$system_max" -gt "40000" ] ; then
		MAX_FILEDESCRIPTORS=16384
	elif [ "$system_max" -gt "10000" ] ; then
		MAX_FILEDESCRIPTORS=8192
	else
		MAX_FILEDESCRIPTORS=1024
		cat << EOF

Warning: Your system has very few filedescriptors available in total.

Maybe you should try raising that by adding 'fs.file-max=100000' to your
/etc/sysctl.conf file.  Feel free to pick any number that you deem appropriate.
Then run 'sysctl -p'.  See /proc/sys/fs/file-max for the current value, and
file-nr in the same directory for how many of those are used at the moment.

EOF
	fi
else
	MAX_FILEDESCRIPTORS=8192
fi

NICE=""

test -x $DAEMON || exit 0

# Include tor defaults if available
if [ -f $DEFAULTSFILE ] ; then
	. $DEFAULTSFILE
fi

wait_for_deaddaemon () {
	pid=$1
	sleep 1
	if test -n "$pid"
	then
		if kill -0 $pid 2>/dev/null
		then
			echo -n "."
			cnt=0
			while kill -0 $pid 2>/dev/null
			do
				cnt=`expr $cnt + 1`
				if [ $cnt -gt $WAITFORDAEMON ]
				then
					echo " FAILED."
					return 1
				fi
				sleep 1
				echo -n "."
			done
		fi
	fi
	return 0
}


check_torpiddir () {
	if test ! -d $TORPIDDIR; then
		echo "There is no $TORPIDDIR directory.  Creating one for you."
		mkdir -m 02700 "$TORPIDDIR"
		chown debian-tor:debian-tor "$TORPIDDIR"
	fi

	if test ! -x $TORPIDDIR; then
		echo "Cannot access $TORPIDDIR directory, are you root?" >&2
		exit 1
	fi
}

check_config () {
	if ! $DAEMON --verify-config > /dev/null; then
		echo "ABORTED: Tor configuration invalid:" >&2
		$DAEMON --verify-config >&2
		exit 1
	fi
}


case "$1" in
  start)
	if [ "$RUN_DAEMON" != "yes" ]; then
		echo "Not starting $DESC (Disabled in $DEFAULTSFILE)."
		exit 0
	fi

	if [ -n "$MAX_FILEDESCRIPTORS" ]; then
		echo -n "Raising maximum number of filedescriptors (ulimit -n) to $MAX_FILEDESCRIPTORS"
		if ulimit -n "$MAX_FILEDESCRIPTORS" ; then
			echo "."
		else
			echo ": FAILED."
		fi
	fi

	check_torpiddir

	echo "Starting $DESC: $NAME..."
	check_config
[/PHP]

Also, it is a shame the whole program just crashes when the ulimit is reached instead of just refusing incoming connections gracefully.

---

### Post by Brandon Williams on 2009-04-29
You can modify the various limits by editing /etc/security/limits.conf. The mods can impact all users on the system, or can be targeted at specific users.

---

### Post by shoeheight on 2009-04-30
Thank you, but I've already tried to modify my etc/security/limits.conf by adding the line:
*	hard	nofile	9000

But no change in ulimit is seen....any suggestions?

---

### Post by Brandon Williams on 2009-04-30
How is your script to start the tor daemon being run? I got the impression that it is not being run at startup, which means that changes to limits.conf should work, since they are applied at login by pam_limits.so.

If you are not logged in when your tor startup script is run, but rather running it via init.d (and therefore as root), then you should be able to simply add a call to ulimit to your startup script.

---

### Post by shoeheight on 2009-04-30
There is no Tor file in the init.d directory, so I am not sure how I can modify my startup script.  

I made/installed vidalia directly out of my home directory, not using the repositories.  It seemed easier at the time to do that. 

I have vidalia run on login by manually adding it to system-preferences-sessions with a "vidalia" command. 

So, where is the startup script that I can modify, and how can I modify it?

Any ideas?

Thanks

PS does anyone know why isn't there an official Tor forum?

---

### Post by Brandon Williams on 2009-04-30
It sound like you have things configured the way that I thought ... the daemon starts up as a result of you logging in and it runs with your user id as the effective user id. If this is the case, then I would expect the changes to limits.conf that you describe to have corrected the open files limit problem. When I make that same change to limits.conf and run a test script as an autostarted application, I can see that my open files limit is the new higher value within my script. If that's not the case for you, I'm not sure what's going wrong and hopefully someone else will comment.

If you want to start the tor daemon when your system starts rather than when you log in, you can add a call to your startup script just before 'exit 0' in /etc/rc.local. Just make sure that /etc/rc.local has execute permission. In this way, the startup script for tor will run as root, which means you can add a ulimit call to the start script to raise the open files limit just for the tor daemon.

---

### Post by shoeheight on 2009-04-30
Thanks anyways. 

I'd love to find that official tor forum

---

### Post by shoeheight on 2009-05-03
anyone else have any ideas?

---

### Post by Jack Waugh on 2010-11-29
Like the original poster, I like to run Vidalia.  It gives me a quick and convenient way to shut down Tor or fiddle with the settings in case I think the demand on my Internet connection is too high for the other user of my local network.

I added these lines to /etc/security/limits.conf:

[HTML]
#<domain>      <type>  <item>         <value>
*              hard    nofile          65000
*              soft    nofile          9000 # help tor
[/HTML]

Maybe the key issue with your change noted above is you also need to set the soft limit.  Now when I log in and do "ulimit -n", I get back 9000, which seems to me to be a good sign.  I haven't run tor for long after setting this, so I can't say for sure whether the warnings are going to come back or not.

---

