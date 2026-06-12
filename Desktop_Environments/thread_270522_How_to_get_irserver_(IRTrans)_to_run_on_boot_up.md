---
title: "How to get irserver (IRTrans) to run on boot up"
date: 2006-10-03
forum: Desktop Environments
---

### Post by billgloff on 2006-10-03
Hi All,

I have a Dapper Drake system running with 0.20 of MythTV on a Origin X11 case which has the IRTrans capatible VFD & IR. Anyways, to get the VFD working, I first run irserver, and then I run LCDd -c LCDd.conf and voila it works. 

My problem is getting this to start up correctly on boot up and not manually like I do now. I tried creating a .sh script with these commands and putting them in the init.d directory and selecting them to start on boot but it doesn't seem to work. Also tried putting them into the Gnome startup sessions and that didn't seem to work either. I know it doesn't work because the VFD doesn't light up until I run the scripts manually.

Anyone know how I can get irserver to start up as a deamon/servive on boot up?

Thanks,
Bill

---

### Post by HaroBlack on 2007-12-03
this is what i use, you'll have to change the usb location ( /dev/yourirserverthing ) and where you put the irserver files.. also the writing pid to a file isn't really needed. please be kind on the code, this is my first attempt at a useful script and i cobbled it together from other scripts.. here it is warts and all, if you don't like it, rewrite it and post it back here.

I call this file startir and put it in my /etc/init.d/ and add it with the rc-update command

```

#!/bin/sh -e
#
# /etc/init.d/startir 

NAME="Irserver"
FNAME="irserver"
PIDNAME="/var/run/irserver.pid"

irserver_start() {
        ( cd /usr/local/irtrans && ./irserver -pidfile ${PIDNAME} -daemon /dev/ttyUSB0 ) &        
        echo "$NAME tried to start"
	irserver_status
}

irserver_stop() { killall $FNAME }

#irserver_reload() {
#        if [[ $(mount | grep -c ${MNT}) > 0 ]]; then
#                echo "Unmounting ${MNT}"
#                umount ${MNT}
#        fi
#        kill -HUP `cat ${PID}` >&/dev/null
#
#        echo "Mounting ${MNT}"
#        sleep 5
#        mount ${MNT}
#        if [[ $? != 0 ]]; then
#                echo "Failed to start jungle disk"
#        fi
#}

irserver_status() {
        TEMPPID=`ps -A | grep irserver | grep -v 'bash\|grep\|mount' | awk '{ print $1 }'`
        if [ "${TEMPPID}" > 0 ]; then
                echo "Running on PID: $TEMPPID"
        else
                echo "Not running"
        fi
}

case $1 in
        start)
                echo "Starting $NAME"
                irserver_start
                exit 0
        ;;
        stop)
                echo "Stopping $NAME"
                irserver_stop
                exit 0
        ;;
#        reload)
#                echo "Reloading $NAME"
#                irserver_reload
#                exit 0
#        ;;
        status)
                irserver_status
                exit 0
        ;;
        *)
                echo "Usage: /etc/init.d/irserver start|stop|status" >&2
                exit 0
        ;;
esac

```

---

