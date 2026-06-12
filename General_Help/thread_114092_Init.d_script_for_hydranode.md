---
title: "Init.d script for hydranode"
date: 2006-01-07
forum: General Help
---

### Post by Cklein on 2006-01-07
Hi, I'm trying a great p2p app: Hydranode [http://hydranode.com]("http://hydranode.com")
I want to start and stop as a service when I boot and shutdown the system. I tried to create a init.d script for hydranode but no luck. I copied the one from ssh and modify to use it with hydranode but it doesn't work:
```

#! /bin/sh
set -e

. /lib/lsb/init-functions


# /etc/init.d/hydranode: start and stop Hydranode

export HYDRANODE=/home/p2p/hydranode/hydranode/hydranode/hydranode
export HNUSER=p2p
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/p2p/hydranode/hydranode/hydranode/lib
export PATH="${PATH:+$PATH:}/usr/sbin:/sbin:/home/p2p/hydranode/hydranode/hydranode"


case "$1" in
  start)
        log_begin_msg "Starting Hydranode..."
       start-stop-daemon --start --quiet --pidfile /var/run/hydranode.pid --chuid $HNUSER --exec $HYDRANODE || log_end_msg 1
        log_end_msg 0
        ;;
  stop)
        log_begin_msg "Stopping Hydranode..."
        start-stop-daemon --stop --quiet --oknodo --pidfile /var/run/hydranode.pid || log_end_msg 1
        log_end_msg 0
        ;;

esac

exit 0

```
The problem is that it doesn't start the program as the 'p2p' user, always as root. Anyone can help me with this??

---

