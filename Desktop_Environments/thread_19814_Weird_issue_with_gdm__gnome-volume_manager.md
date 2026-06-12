---
title: "Weird issue with gdm / gnome-volume manager?"
date: 2005-03-13
forum: Desktop Environments
---

### Post by Redemption042 on 2005-03-13
When I boot up, gdm starts up and logs me in which brings up the little gnome startup box.  Right after the box dissappears and the top and bottom panels appear my system stops for about 1 min with nothing on the screen but the brown backgroud, and the two (empty) top and bottom panels.   

Then, after about a minute, the rest of my desktop appears and works as if nothing happened.  If I stick in a CD or a memory stick into my MS reader, it will not be automounted, but I can mount it manually.  Though, If I do mount it manually, nothing will appear on my desktop.   

Now, the weirdness starts.  If I kill gdm from a terminal, then restart gdm it will start up without the minute delay and automount will work fine.    The problems ONLY occur when I'm running gdm from start-up.  

I'm running haory with the 6629 nvidia drivers installed and can post any other info anyone might request.   

At first I thought the problem was that gdm was being started to early in the boot up sequence (i.e. S13gdm, rather then S99gdm. But I changed it and it didn't make a difference.

---

### Post by Redemption042 on 2005-03-13
the problem seems to be in /lib/lsb/init-functions.

this is my standard /etc/init.d/gdm file

----------------------------------
#! /bin/sh
#
# Originally based on:
# Version:	@(#)skeleton  1.8  03-Mar-1998  [email]miquels@cistron.nl[/email]
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
DAEMON=/usr/bin/gdm
PIDFILE=/var/run/gdm.pid
UPGRADEFILE=/var/run/gdm.upgrade

if [ -e $UPGRADEFILE -a "$1" != "restart" -a "$1" != "force-reload" ]; then
	SSD_ARG="--startas $DAEMON"
	rm -f $UPGRADEFILE
else
	SSD_ARG="--exec $DAEMON"
fi

test -x $DAEMON || exit 0

if [ -r /etc/default/gdm ]; then
  . /etc/default/gdm
  if [ -z "$LANG" ]; then
    :
  else
    export LANG
  fi
fi

. /lib/lsb/init-functions

case "$1" in
  start)
  	if [ -e "$DEFAULT_DISPLAY_MANAGER_FILE" -a "$HEED_DEFAULT_DISPLAY_MANAGER" = "true" -a "$(cat $DEFAULT_DISPLAY_MANAGER_FILE)" != "$DAEMON" ]; then
		log_warning_msg "Not starting GNOME Display Manager (gdm); it is not the default display manager."
	else
		log_begin_msg "Starting GNOME Display Manager..."
		start-stop-daemon --start --quiet --pidfile $PIDFILE --name gdm $SSD_ARG >/dev/null 2>&1 || log_end_msg 1
		log_end_msg 0
	fi
  ;;
  stop)
	log_begin_msg "Stopping GNOME Display Manager..."
	start-stop-daemon --stop  --quiet --pidfile $PIDFILE --name gdm $SSD_ARG --retry 30 >/dev/null 2>&1 || \
		log_warning_msg "GNOME Display Manager not running"
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

------------------------------------
but, when I comment out the line '. ./lib/lsb/init-functions' and reboot.
gdm loads fine without the one minute pause.  But,  automount doesn't work,  even if I kill gdm, CTRL-ALT-BKSPC to the cli, and restart gdm.

But, if I don't have that line commented out when I start up, then I have the one minute pause when starting gdm at, and only at, bootup.  but, for some reason, when I kill gdm, CTRL-ALT_BKSPC to the CLI and startup gdm manually, automounting works fine.

Though, I may be going crazy.  I'm not certain.  Automount seems to want to work completely randomly, and I have no idea why /lib/lsb/init-functions would have any affect whatsover, but it does.

---

### Post by Redemption042 on 2005-03-13
For some reason, when I start up the computer with the standard GDM  script in /etc/init.d/gdm  gnome-volume-manger fails to start up, even though it's set to do so in the session manager.  So, if I bring up a console and type 'gnome-volume-manager' I will have automounting.

So, something about /lib/lsb/init-functions somehow breaks gnome-volume-manager, in that it causes it not to start, and fixes gnome-volume-manager in that if init-functions is not run, gnome-volume-manager won't work.  

Could someone please help me here.  I have no idea why gnome-volume-manager won't work if gdm is not started with /etc/init.d/gdm and I have no idea why gnome-volume-manager won't start up with the rest of the session when gdm is started up with /etc/init.d/gdm


help me obi wan kinobi, you're my only hope.

---

