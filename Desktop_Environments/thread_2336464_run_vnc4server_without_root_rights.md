---
title: "run vnc4server without root rights????"
date: 2016-09-08
forum: Desktop Environments
---

### Post by CrewDK on 2016-09-08
In my local network I'm helping my users through vnc4server. I'm running it on :0 display so this works really like remote display (like teamviewer or radmin on windows systems). 
I created service that should be run every time when user logs into system. And my problem is that everything works fine on ubuntu 14.04 but it stops working on 16.04. 
Every time user trying to run this service (manualy or automatic during startup) system asks about root privileges! 

```
$ /etc/init.d/vnc0 start
[....] Starting vnc0 (via systemctl): vnc0.service==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ===
Authentication is required to start 'vnc0.service'.
Authenticating as: root
Password: 

$ service vnc0 start
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ===
Authentication is required to start 'vnc0.service'.
Authenticating as: root
Password:
```

And my script itself: 


```

#!/bin/sh
### BEGIN INIT INFO
# Provides: vncserver
# Required-Start: networking
# Required-Stop: $all
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: x0vnc4launcher
# Description:
### END INIT INFO
            
PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"
                
USER=$(ps aux | grep xfce4-session | grep -v grep | awk '{print $1}')
ADDR=$(ip route | grep src | awk '{print $9}')
                
# The display that VNC will use
DISPLAY="0"
                
OPTIONS="-display :${DISPLAY}"
                
. /lib/lsb/init-functions

case "$1" in
            
start)
  sleep 5
  log_action_begin_msg "Starting vncserver for user '${USER}' on ${ADDR}:${DISPLAY}"
  su ${USER} -c "x0vnc4server ${OPTIONS} -PasswordFile ~/.vnc/passwd &" > /dev/null 2>&1
  sleep  5
  ;;

stop)
  log_action_begin_msg "Stoping vncserver for user '${USER}' on ${ADDR}:${DISPLAY}"
  killall x0vnc4server
  ;;

restart)
  $0 stop
  $0 start
  ;;

*)
  echo "Usage: /etc/init.d/vnc0 {start|stop|restart}"
  exit 1
esac
exit 0

```

So what i did wrong? Why this fine works on 14.04? And maybe there is any another way to connect to real users display with vnc server?

---

