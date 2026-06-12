---
title: "Aborting configuration of an interface from if-pre-up.d"
date: 2005-06-09
forum: Desktop Environments
---

### Post by simbaB on 2005-06-09
I would like to prevent my wireless interface from coming up when an Ethernet cable is plugged in. I would like to do this from within the ifupdown system, so that 'ifup eth0' (eth0=wireless eth1=ethernet) exits with an error when there is a link on eth1. Simply doing an 'exit 1' in an if-pre-up.d script doesn't help--ifup keeps on going. The best solution I could come up with was the script below, it's horrible and hacky and as you can see, it might kill other ifup or run-parts processes as well:


```

#!/bin/sh

case $IFACE in
        eth0)
                if ethtool eth1 | grep -q "Link detected: yes"; then
                        echo "There seems to be an Ethernet cable plugged in. I will not"
                        echo "start the wireless connection."
                        kill `pidof ifup`
                        kill `pidof run-parts`
                        exit 1
                fi
        ;;
esac

exit 0

```

Is there a better way to do this? Thanks for any tips or help anyone can offer.

Andrew

---

### Post by simbaB on 2005-06-10
I figured it out--so here's what I did in case anyone stumbles across this thread:

The request for this feature is [Debian bug #88945](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=88945). Unfortunately this bug is over four years old, but fortunately there are some ifupdown packages at [http://q.bofh.de/~mh/debian/ifupdown/](http://q.bofh.de/~mh/debian/ifupdown/) that offer functionality that comes close. These packages will abort ifupdown if the script is invoked from /etc/network/interfaces and exits with a non-zero return code. This is opposed to a script or symlink in /etc/network/if-<action>.d/. Also, it will not deconfigure or reconfigure an interface if used with 'up' or 'down' directives in /etc/network/interfaces.

I recompiled the ifupdown package from source, so I do not know if the .deb binary package on that site works for Ubuntu.

Finally, *don't* try the script I originally posted. On bootup, it will kill 'ifup -a' if there is a link on eth1 (according to ethtool). This has far-reaching implications as the local loopback interface (lo) isn't brought up. I had everything from stuck startup scripts (nfs-kernel-daemon sat there for 30+ seconds) to Gnome hanging on login.

Andrew

---

