---
title: "GDM won't install /etc/init.d/gdm"
date: 2006-07-08
forum: Desktop Environments
---

### Post by sys on 2006-07-08
Hi 

 I had problems with GDM and did "apt-get remove gdm" and "apt-get install gdm" again. Now the /etc/init.d/gdm file is missing, thougth dpkg-query -L gdm lists the file.

How comes this? Can somebody provide me with a file?

greetings
fabian

---

### Post by aysiu on 2006-07-08
Did you try this? ```
sudo apt-get install --reinstall gdm
```

---

### Post by sys on 2006-07-08
Yes, I tried that.

---

### Post by aysiu on 2006-07-08
This is what mine looks like. I'm not sure it'll work on your system, but I guess it's worth a shot: ```
#! /bin/sh
#
# Originally based on:
# Version:	@(#)skeleton  1.8  03-Mar-1998  miquels@cistron.nl
#
# Modified for gdm, Steve Haslam <steve@arise.dmeon.co.uk> 14mar99
# modified to remove --exec, as it does not work on upgrades. 18jan2000
# modified to use --name, to detect stale PID files 18mar2000
# sleep until gdm dies, then restart it 16jul2000
# get along with other display managers (Branden Robinson, Ryan Murray) 05sep2001

set -e

# To start gdm even if it is not the default display manager, change
# HEED_DEFAULT_DISPLAY_MANAGER to "false."
HEED_DEFAULT_DISPLAY_MANAGER=true
DEFAULT_DISPLAY_MANAGER_FILE=/etc/X11/default-display-manager
PATH=/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/gdm
PIDFILE=/var/run/gdm.pid
UPGRADEFILE=/var/run/gdm.upgrade

if [ -e $UPGRADEFILE -a "$1" != "restart" -a "$1" != "force-reload" ]; then
	SSD_ARG="--startas $DAEMON"
	rm -f $UPGRADEFILE
else
	SSD_ARG="--exec $DAEMON"
fi

# Allow cdd to override the config
if [ -f /etc/gdm/gdm-cdd.conf ]; then
	CONFIG_FILE="--config=/etc/gdm/gdm-cdd.conf"
fi

test -x $DAEMON || exit 0

if [ -r /etc/environment ]; then
  if LANG=$(pam_getenv -l LANG); then
    export LANG
  fi
  if LANGUAGE=$(pam_getenv -l LANGUAGE); then
    export LANGUAGE
  fi

fi

. /lib/lsb/init-functions

case "$1" in
  start)
  	if [ -e "$DEFAULT_DISPLAY_MANAGER_FILE" -a "$HEED_DEFAULT_DISPLAY_MANAGER" = "true" -a "$(cat $DEFAULT_DISPLAY_MANAGER_FILE 2>/dev/null)" != "$DAEMON" ]; then
		log_warning_msg "Not starting GNOME Display Manager (gdm); it is not the default display manager."
	else
		# if usplash is runing, make sure to stop it now, yes "start" kills it.
	        if pidof usplash > /dev/null; then
			/etc/init.d/usplash start
		fi
		log_begin_msg "Starting GNOME Display Manager..."
		start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --name gdm $SSD_ARG -- $CONFIG_FILE >/dev/null 2>&1 || log_end_msg 1
		log_end_msg 0
	fi
  ;;
  stop)
	log_begin_msg "Stopping GNOME Display Manager..."
	start-stop-daemon --stop  --quiet --oknodo --pidfile $PIDFILE --name gdm $SSD_ARG --retry 30 >/dev/null 2>&1
	log_end_msg 0
  ;;
  reload)
	log_begin_msg "Reloading GNOME Display Manager configuration..."
	log_warning_msg "Changes will take effect when all current X sessions have ended."
	start-stop-daemon --stop --signal USR1 --quiet --pidfile \
		$PIDFILE --name gdm $SSD_ARG >/dev/null 2>&1
	log_end_msg 0
  ;;
  restart|force-reload)
	$0 stop || true
	$0 start
  ;;
  *)
	log_success_msg "Usage: /etc/init.d/gdm {start|stop|restart|reload|force-reload}"
	exit 1
  ;;
esac

exit 0
```

---

### Post by sys on 2006-07-09
Thanks, it worked.

Strange that ubuntu doesn't install the gdm script by it's own...


greetings
-f

---

