---
title: "problem shuting down console-kit-daemon"
date: 2009-05-05
forum: General Help
---

### Post by accaacca on 2009-05-05
I've installed Jaunty and I noticed a problem: shuting down the computer produce a strange system sound. So I checked the log and find in daemon.log this lines:

```
May  5 23:46:00 fury console-kit-daemon[2716]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  5 23:46:01 fury last message repeated 7 times
May  5 23:46:01 fury init: tty4 main process (2252) killed by TERM signal
May  5 23:46:01 fury init: tty5 main process (2253) killed by TERM signal
May  5 23:46:01 fury init: tty2 main process (2258) killed by TERM signal
May  5 23:46:01 fury init: tty3 main process (2259) killed by TERM signal
May  5 23:46:01 fury init: tty6 main process (2260) killed by TERM signal
May  5 23:46:01 fury init: tty1 main process (3227) killed by TERM signal
May  5 23:46:01 fury console-kit-daemon[2716]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
May  5 23:46:01 fury last message repeated 4 times
May  5 23:46:01 fury NetworkManager: <info>  (wlan0): device state change: 8 -> 3 
May  5 23:46:01 fury NetworkManager: <info>  (wlan0): deactivating device (reason: 38). 
May  5 23:46:01 fury NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 3576 
May  5 23:46:01 fury NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
May  5 23:46:01 fury avahi-daemon[2954]: Withdrawing address record for 192.168.1.140 on wlan0.
May  5 23:46:01 fury avahi-daemon[2954]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.140.
May  5 23:46:01 fury avahi-daemon[2954]: Interface wlan0.IPv4 no longer relevant for mDNS.
May  5 23:46:02 fury console-kit-daemon[2716]: WARNING: Unable to activate console: No such device or address 
May  5 23:46:02 fury console-kit-daemon[2716]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `<invalid>' 
May  5 23:46:02 fury console-kit-daemon[2716]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
May  5 23:46:02 fury console-kit-daemon[2716]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
```as you can notice there is something about console-kit-daemon, what's wrong with it?

thanks

---

### Post by Eugene_ on 2009-05-23
I don't know have you seen this or not:
[https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/374397](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/374397)
The solution should be there in time.

Or if you find solution by yourself please post it there. We all want to get rid of this sound!

---

