---
title: "launch x app from Networkmanager dispatcher.d"
date: 2009-05-23
forum: General Help
---

### Post by Boondoklife on 2009-05-23
I am trying to open a gkrellm instance to monitor a server when I am connected to a network in which it can be reached. I have come across a couple of pages that talk about setting proxies from /etc/Networkmanager/dispatcher.d and am trying to work from this base to get it done.

Here is what I have come up with for now.
```
#!/bin/bash

#Diese Werte werden vom NetworkManager an das Skript übergeben
INTERFACE=$1
ACTION=$2

#Hauptbenutzer finden
ON_USER=$(cat /etc/passwd | grep :1000: | cut -d ':' -f 1)
#Assumes user directory is /home/$ON_USER
export DBUS_SESSION=$(grep -v "^#" /home/$ON_USER/.dbus/session-bus/`cat /var/lib/dbus/machine-id`-0)

#echo $ON_USER

PING=`ping elohim -c 1 | grep received | awk '{print $4}'`


## Funktionen durchführen, je nach Aktion eine andere
echo "init" > /tmp/gg
if [ $PING -gt 0 ]; then
    echo "Connected" >> /tmp/gg
    echo "sudo -u DISPLAY=:0.0; $ON_USER; $DBUS_SESSION; gkrellm -s elohim&;" >> /tmp/gg

    sudo -u $ON_USER $DBUS_SESSION DISPLAY=:0.0 gkrellm -s elohim

fi
```

I can check in /tmp/gg and do see that it is being ran and the logic for the ping etc are working, but I never get the gkrellm window open on my desktop. I would assume this is possible I just can not seem to find a way to do it.

---

### Post by Boondoklife on 2009-05-26
Really, no one?

---

### Post by Boondoklife on 2009-05-28
For anyone that was looking to do something similar then here ya go I figured it out.

I had to make this a two part script as I could not get su -c to return the pid of the executable with out wrapping it in another script.

This pings a host to see if it is available when Networkmanager makes a connection and if it is then it launches gkrellm to monitor that server. when you disconnect a connection it checks again and if it can not reach the server it closes the monitor.

/etc/NetworkManager/dispatcher.d/99gkrellm_launcher```
#!/bin/bash

PING=`ping -c 2 elohim | grep received | awk '{print $4}'`
SERVER=server
USER=user
PIDFILE=/home/${USER}/.gkrellm_monitor_$SERVER 

if [ $PING -gt 0 ]; then
    su ${USER} -c "gkrellm_monitor ${USER} ${SERVER}"

else
    kill `cat $PIDFILE`
fi

```*** IMPORTANT:** You must specify the username you will be logged in with on your client system.

/usr/bin/gkrellm_monitor```
#!/bin/bash

USER=$1
SERVER=$2

DISPLAY=":0.0" gkrellm -s ${SERVER}&
echo $! > /home/${USER}/.gkrellm_monitor_$SERVER

```

---

