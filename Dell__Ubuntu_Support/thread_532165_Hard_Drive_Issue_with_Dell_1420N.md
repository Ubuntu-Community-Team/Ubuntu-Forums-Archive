---
title: "Hard Drive Issue with Dell 1420N?"
date: 2007-08-22
forum: Dell  Ubuntu Support
---

### Post by cheetaux on 2007-08-22
In the Hardware and Laptops forum, there is a rather detailed thread on issues with how Ubuntu handles hard drives during shutdown.

The thread is labeled:  "Ubuntu is killing your hdd!". 

The following is part of the first post in this thread:

> Yes, this is it. Ubuntu is killing my (and eventually yours) hard drive!

My machine is a HP ze4950 laptop. I have ran Kubuntu in it for a day only, since I noticed a very grave bug.

It happens Ubuntu (and Gentoo, as far as I can tell) kills your hdd's. This is because upon power off, the kernel sends the FLUSH CACHE message to the disk to flush the disk write cache, which cause it to spin up. Then it suddenly shuts down making no call to the STANDBY signal to make the disk stop. The result is that the hdd keeps spinning as the power is off. Modern hdd's (yours, if it works after rebooting), can prevent such damage by taking the head off the disk surface just after power down so it does not hurt the disk in such situation. This is called an emergency unload. Technical specifications say doing this instead of the regular standby can reduce the drive's life time by about a rate of thrity (30) times. The symptoms of this is a weird noise upon shutdown (power off). It is like a "pop"!

Question: Does any here know is this is a real issue and if so, does it exist on the 1420N notebook.

---

### Post by dmarsh on 2007-08-22
I also noticed this problem.  It is easily fixed by a modification to the halt script in /etc/init.d.  If you edit this script, you should add the lines shown just previous to the actual halt command:


        # cache halt command
        cat /sbin/halt > /dev/null

        log_action_msg "Will now halt"
        
        # Added to gently shutdown hard disk
        #  Ask the disk to flush its write cache
        hdparm -f /dev/sda
        sleep 1
        #  Ask the disk to go to standby (spin down)
        hdparm -y /dev/sda
        sleep 1
        # end of modification

        halt -d -f -i $poweroff $hddown

---

### Post by cheetaux on 2007-08-23
Thanks.  I will have to try that.  I ordered the 1420 notebook but have not received it yet (I also run Ubuntu on my desktop - Dell Dimension E510)

---

### Post by inchaos on 2007-08-23
> **dmarsh said:**
> If you edit this script, you should add the lines shown just previous to the actual halt command:



Okay, I also noticed this "pop" upon shutdown.  
I'm looking at my halt script, (/etc/init.d/halt) but which is the actual halt command and where exactly am I supposed to insert this text?   I don't want to screw anything up--I'm kind of an Ubuntu noob.

Here's what I have (though I'm sure yours is the same, but just in case):


#! /bin/sh
### BEGIN INIT INFO
# Provides:          halt
# Required-Start:    umountroot
# Required-Stop:
# Should-Start:      lvm raid2
# Should-Stop:
# Default-Start:     0
# Default-Stop:
# Short-Description: Execute the halt command.
# Description:
### END INIT INFO

PATH=/usr/sbin:/usr/bin:/sbin:/bin
[ -f /etc/default/halt ] && . /etc/default/halt

. /lib/lsb/init-functions

do_stop () {
	if [ "$INIT_HALT" = "" ]
	then
		case "$HALT" in
		  [Pp]*)
			INIT_HALT=POWEROFF
			;;
		  [Hh]*)
			INIT_HALT=HALT
			;;
		  *)
			INIT_HALT=POWEROFF
			;;
		esac
	fi

	# See if we need to cut the power.
	if [ "$INIT_HALT" = "POWEROFF" ] && [ -x /etc/init.d/ups-monitor ]
	then
		/etc/init.d/ups-monitor poweroff
	fi

	# Don't shut down drives if we're using RAID.
	hddown="-h"
	if grep -qs '^md.*active' /proc/mdstat
	then
		hddown=""
	fi

	# If INIT_HALT=HALT don't poweroff.
	poweroff="-p"
	if [ "$INIT_HALT" = "HALT" ]
	then
		poweroff=""
	fi

	log_action_msg "Will now halt"
	sleep 1
	halt -d -f -i $poweroff $hddown
}

case "$1" in
  start)
	# No-op
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	do_stop
	;;
  *)
	echo "Usage: $0 start|stop" >&2
	exit 3
	;;
esac

:

---

