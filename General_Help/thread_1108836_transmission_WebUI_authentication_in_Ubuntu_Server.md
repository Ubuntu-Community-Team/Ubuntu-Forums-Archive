---
title: "transmission WebUI authentication in Ubuntu Server"
date: 2009-03-28
forum: General Help
---

### Post by mha2908 on 2009-03-28
Hi, I'm running a headless Ubuntu Server, and finally I made a startscript which starts transmission-daemon on boot. This makes it possible to open the Transmission WebUI from any computer elsewhere. BUT: I can't make any authentication. This is my settings file (i think - grabbed from /home/myusername/.config/transmission-daemon/settings.json):

```
                                
{
    "blocklist-enabled": 0,
    "download-dir": "\/etc",
    "download-limit": 100,
    "download-limit-enabled": 0,
    "encryption": 1,
    "max-peers-global": 200,
    "peer-port": 51413,
    "pex-enabled": 1,
    "port-forwarding-enabled": 0,
    "rpc-access-control-list": "+127.0.0.1",
    "rpc-authentication-required": 1,
    "rpc-password": "mypassword",
    "rpc-port": 9091,
    "rpc-username": "myusername",
    "upload-limit": 100,
    "upload-limit-enabled": 0
}l

```

Is it the right settingsfile? I mean, the daemon is started on boot with this script:

```

#!/bin/sh.

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME="Transmission"
DESC="torrent daemon"

case "$1" in
        start)
                echo -n "Starting $DESC: "
                transmission-daemon
                echo "$NAME."
                ;;
        stop)
                echo -n "Stopping $DESC: "
                killall transmission-daemon
                echo "$NAME."
                ;;
        *)
                N=/etc/init.d/$NAME
                echo "Usage: $N {start|stop}" >&2
                exit 1
                ;;
esac
exit 0

```

Where the hell does it get it's settings from? Just a thought: outside my home folder somewhere?

By the way - i'm NOT using lighttpd which i ran into in many guides about setting it up. I use Apache2 but I don't know if it makes much of a difference. Plz help me about this, and feel free to ask!

---

### Post by mha2908 on 2009-03-28
Hi, I'm running a headless Ubuntu Server, and finally I made a startscript which starts transmission-daemon on boot. This makes it possible to open the Transmission WebUI from any computer elsewhere. BUT: I can't make any authentication. This is my settings file (i think - grabbed from /home/myusername/.config/transmission-daemon/settings.json):

```
                                
{
    "blocklist-enabled": 0,
    "download-dir": "\/etc",
    "download-limit": 100,
    "download-limit-enabled": 0,
    "encryption": 1,
    "max-peers-global": 200,
    "peer-port": 51413,
    "pex-enabled": 1,
    "port-forwarding-enabled": 0,
    "rpc-access-control-list": "+127.0.0.1",
    "rpc-authentication-required": 1,
    "rpc-password": "mypassword",
    "rpc-port": 9091,
    "rpc-username": "myusername",
    "upload-limit": 100,
    "upload-limit-enabled": 0
}l

```

Is it the right settingsfile? I mean, the daemon is started on boot with this script:

```

#!/bin/sh.

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME="Transmission"
DESC="torrent daemon"

case "$1" in
        start)
                echo -n "Starting $DESC: "
                transmission-daemon
                echo "$NAME."
                ;;
        stop)
                echo -n "Stopping $DESC: "
                killall transmission-daemon
                echo "$NAME."
                ;;
        *)
                N=/etc/init.d/$NAME
                echo "Usage: $N {start|stop}" >&2
                exit 1
                ;;
esac
exit 0

```

Where the hell does it get it's settings from? Just a thought: outside my home folder somewhere?

By the way - i'm NOT using lighttpd which i ran into in many guides about setting it up. I use Apache2 but I don't know if it makes much of a difference. Plz help me about this, and feel free to ask!

---

### Post by overdrank on 2009-03-28
Please do not create multiple threads on the same issue. Threads merged.

---

### Post by sisco311 on 2009-03-28
> **mha2908 said:**
> 

Where the hell does it get it's settings from? Just a thought: outside my home folder somewhere?



the init.d script runs as root. 
and reads the settings from /root/.config/blabla

it's probably better to run the daemon as a non-root user:
```
su - username -c transmission-daemon
```
if you run it as your user, then it will read the settings from your $HOME directory.

---

### Post by mha2908 on 2009-03-28
allright, first i replaced

```

        start)
                echo -n "Starting $DESC: "
                transmission-daemon
                echo "$NAME."
                ;;

```

with

```

        start)
                echo -n "Starting $DESC: "
                su - myusername -c transmission-daemon
                echo "$NAME."
                ;;

```

but that returned an error. Maybe you misspelled something: "su - ", but i'm a TOTAL NOOB, so I don't know!

Then i changed it back and edited the /root/.config/transmission-daemon/settings.json - but everytime it boots the file changes back to default, making the RCP-settings disabled. WTF do I do?

---

### Post by jam-2000 on 2009-06-21
use this guide...
[http://philsturgeon.co.uk/news/2009/02/How-to-Install-Transmission-CLI-to-Ubuntu-Server.html](http://philsturgeon.co.uk/news/2009/02/How-to-Install-Transmission-CLI-to-Ubuntu-Server.html)

---

