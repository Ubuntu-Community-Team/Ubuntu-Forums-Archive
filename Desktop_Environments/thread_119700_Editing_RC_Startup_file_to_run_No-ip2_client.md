---
title: "Editing RC Startup file to run No-ip2 client"
date: 2006-01-20
forum: Desktop Environments
---

### Post by jscrilla on 2006-01-20
Hello all! 

I'm new to Ubuntu...my first linux client. I'm loving it so far. This is day two of hacking away at it. 

Ok, enough mushy stuff. Here's my issue. 

I've installed the no-ip2 client which is currently running as a daemon in the background. I would like to ensure that it runs upon restart. The readme file has instructions on how to update the rcX file, which I gedited but didn't want to change. I'm not a programmer so its kind of confusing where to put the code they gave me. Can someone help me out here? I've included the code snippets below. Oh, and I've backed up the rc file to rc_backup. :)

**The snippet from the readme.first file**

HOW TO START THE CLIENT

The noip2 executable can be run by typing /usr/local/bin/noip2

If you want it to run automatically when the machine is booted, then
place the following script in your startup directory. (/etc/init.d/rcX.d
or /sbin/init.d/rcX.d or ???) 

	#######################################################
	#! /bin/sh
	# . /etc/rc.d/init.d/functions	# uncomment/modify for your killproc
	case "$1" in
	    start)
		echo "Starting noip2."
		/usr/local/bin/noip2
	    ;;
	    stop)
		echo -n "Shutting down noip2."
		killproc -TERM /usr/local/bin/noip2
	    ;;
	    *)
		echo "Usage: $0 {start|stop}"
		exit 1
	esac
	exit 0
	#######################################################

Where the 'X' in rcX.d is the value obtained by running the 
following command
	grep initdefault /etc/inittab | awk -F: '{print $2}'

Killproc can be downloaded from [ftp://ftp.suse.com/pub/projects/init](ftp://ftp.suse.com/pub/projects/init)
Alternatively, you can uncomment the line after #! /bin/sh

If you have a recent RedHat version, you may want to use the startup script
supplied by another user.  It's in this package called redhat.noip.sh
It may need some modification for your system.

There is a startup script for Debian called debian.noip2.sh.
It also has been supplied by another user and is rumored to fail in some
situations.

Here is a script which will kill all running copies of noip2.
  #!/bin/sh
  for i in `noip2 -S 2>&1 | grep Process | awk '{print $2}' | tr -d ','`
  do
    noip2 -K $i
  done
These four lines can replace 'killproc' and 'stop_daemon' in the other scripts.

If you are behind a firewall, you will need to allow port 8245 (TCP) through
in both directions.

**The RC file on my system**

#! /bin/sh
#
# rc		This file is responsible for starting/stopping
#		services when the runlevel changes.
#
#		Optimization feature:
#		A startup script is _not_ run when the service was
#		running in the previous runlevel and it wasn't stopped
#		in the runlevel transition (most Debian services don't
#		have K?? links in rc{1,2,3,4,5} )
#
# Author:	Miquel van Smoorenburg <miquels@cistron.nl>
#		Bruce Perens <Bruce@Pixar.com>
#
# Version:	@(#)rc  2.78  07-Nov-1999  [email]miquels@cistron.nl[/email]
#

# Un-comment the following for debugging.
# debug=echo

#
# Start script or program.
#
startup() {
  case "$1" in
	*.sh)
		$debug sh "$@"
		;;
	*)
		$debug "$@"
		;;
  esac
}

  # Ignore CTRL-C only in this shell, so we can interrupt subprocesses.
  trap ":" INT QUIT TSTP

  # Set onlcr to avoid staircase effect.
  stty onlcr 0>&1

  # Now find out what the current and what the previous runlevel are.

  runlevel=$RUNLEVEL
  # Get first argument. Set new runlevel to this argument.
  [ "$1" != "" ] && runlevel=$1
  if [ "$runlevel" = "" ]
  then
	echo "Usage: $0 <runlevel>" >&2
	exit 1
  fi
  previous=$PREVLEVEL
  [ "$previous" = "" ] && previous=N

  export runlevel previous

  # Is there an rc directory for this new runlevel?
  if [ -d /etc/rc$runlevel.d ]
  then
	# First, run the KILL scripts.
	if [ $previous != N ]
	then
		for i in /etc/rc$runlevel.d/K[0-9][0-9]*
		do
			# Check if the script is there.
			[ ! -f $i ] && continue

			# Stop the service.
			startup $i stop
		done
	fi
	# Now run the START scripts for this runlevel.
        steps=$(echo /etc/rc$runlevel.d/S*)
        num_steps=0
        for step in $steps; do
            num_steps=$(($num_steps + 1))
            case "${step##/etc/rc$runlevel.d/S??}" in
                gdm|xdm|kdm)
                    break
                    ;;
            esac
        done
        current_step=0

	for i in $steps
	do
		[ ! -f $i ] && continue

		if [ $previous != N ] && [ $previous != S ]
		then
			#
			# Find start script in previous runlevel and
			# stop script in this runlevel.
			#
			suffix=${i#/etc/rc$runlevel.d/S[0-9][0-9]}
			stop=/etc/rc$runlevel.d/K[0-9][0-9]$suffix
			previous_start=/etc/rc$previous.d/S[0-9][0-9]$suffix
			#
			# If there is a start script in the previous level
			# and _no_ stop script in this level, we don't
			# have to re-start the service.
			#
			[ -f $previous_start ] && [ ! -f $stop ] && continue
		fi
		case "$runlevel" in
			0|6)
				startup $i stop
				;;
			*)
				startup $i start
				;;
		esac
                last_step=$(($last_step + 1))
                # 50% of progress for rcS, 50% for our ultimate runlevel
                progress=$(($last_step * 50 / $num_steps + 50))
                if type usplash_write >/dev/null 2>&1; then
                    usplash_write "PROGRESS $progress" || true
                fi
	done
  fi
# eof /etc/init.d/rc

---

### Post by slashem on 2006-01-20
You only need what is between the ############################################# lines as far as I can see.

#!/bin/sh has to be on the very first line

Paste that into gedit and save as /etc/init.d/local-no-ip2 or whatever you want to call it.
Then do this:

sudo chmod +x /etc/init.d/local-no-ip2
cd /etc/rc2.d
sudo ln -s ../init.d/local-no-ip2 S99local-no-ip2
cd /etc/rc3.d
sudo ln -s ../init.d/local-no-ip2 S99local-no-ip2
cd /etc/rc4.d
sudo ln -s ../init.d/local-no-ip2 S99local-no-ip2
cd /etc/rc5.d
sudo ln -s ../init.d/local-no-ip2 S99local-no-ip2
/etc/init.d/local-no-ip2 start #if you want to start the service now

---

### Post by LordBug on 2006-01-20
Create a file called "noip2" and put that script into it.  Make it executible, and put it in /etc/init.d  (you'll need root for that)

> grep initdefault /etc/inittab | awk -F: '{print $2}'

Run that like it said.  Then create a symlink in /etc/init.d/rc?.d pointing to /etc/init.d/noip2.  It should start on bootup now, unless I missed something :)

*edit*  Looks like Slashem responded as I was.

---

### Post by jscrilla on 2006-01-20
Thanks for your help! I'll give it a try when I get home. :)

---

