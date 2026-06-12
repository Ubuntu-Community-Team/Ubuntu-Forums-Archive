---
title: "adding a daemon on startup??"
date: 2005-01-04
forum: Desktop Environments
---

### Post by amandla on 2005-01-04
I install a daemon on my laptop to enable its special keys ( +/- screen brightness etc). I was wondering how to get the daemon to run automatically on startup. I figure I would have to edit /etc/rc#.d/ but they are all links to scripts and the daemon is a binary. Its the fnfx daemon for toshiba laptops.

Anyone know how?

---

### Post by zeroK on 2005-01-04
[QUOTE=amandla]I install a daemon on my laptop to enable its special keys ( +/- screen brightness etc). I was wondering how to get the daemon to run automatically on startup. I figure I would have to edit /etc/rc#.d/ but they are all links to scripts and the daemon is a binary. Its the fnfx daemon for toshiba laptops.

Anyone know how?[/QUOTE]
 In this case you will have to write a small init script (written in bash) for it. In the end they are not much more than big switches:
```
case "$1" in
  start)
	# Executed during startup
	;;
  stop)
	# Executed when stopping the service
	;;


  restart)
        # Normally not much more than stop and start executed sequencially
	;;
esac
```

---

### Post by amandla on 2005-01-05
ok i created one, but i am not to sure if it will work. I have to copy it into /etc/init.d/ and create a like to it in /etc/rc5.d/ correct???

here is the script:
```

#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin
DAEMON=/usr/local/sbin/fnfxd
NAME=FNFX
DESC=FNFX

test -x $DAEMON || exit 0

check_modules_loaded() {
	TOSHIBA=/proc/acpi/toshiba
	ACPI=/proc/acpi

	if [ -f $TOSHIBA || -f $ACPI]
	then
		return 0
	else
		return 1
	fi
}

start(){
	if check_modules_loaded()
	then 
	then
		start-stop-daemon --start --quiet --oknodo --exec $DAEMON || return 1
	else
		return 0
	fi
}

case "$1" in
  start)
        log_begin_msg "Starting $DESC... "
	start
        log_end_msg $?
	;;
  stop)
	log_begin_msg "Stopping $DESC: "
	#start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
	log_end_msg $?
	;;
  restart|force-reload)
        $0 stop
	sleep 1
	start
	echo "$NAME."
	;;

esac

exit 0

```

is this correct???

---

