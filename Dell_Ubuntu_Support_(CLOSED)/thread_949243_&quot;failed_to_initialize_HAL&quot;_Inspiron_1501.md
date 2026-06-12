---
title: "&quot;failed to initialize HAL&quot;: Inspiron 1501"
date: 2008-10-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pointfive on 2008-10-16
Hi all. I've been running Ubuntu Hardy on a Dell Inspiron 1501 for a few weeks. Just today I began to get an error after logging in: "Internal error: failed to initialize HAL!" My battery and network taskbar icons are gone, and if I click the power-down button, the gui pretty much hangs and I have to do a hard reboot.

Doing some research led me to try:
```
sudo /etc/init.d/dbus restart
```

This shuts a bunch of things down with an [OK] message, but when it reaches "Starting system message bus dbus", it gives a message: 'Failed to start message bus: the pid file "/usr/var/run/dbus/pid" exists, if the message bus is not running, remove this file.'

So I obediently delete the pid file and try again. This time it seems to go more successfully, until it reaches "Starting Avahi mDNS/DNS-SD Daemon avahi-daemon", which returns a [[COLOR="DarkRed"]fail[/COLOR]] with a footnote of "Can't start Hardware abstraction layer - please ensure dbus is running."

Please help me diagnose this issue. Most of my searches turn up results related to Fiesty and earlier releases.

Last night I was working on installing FFADO drivers, so I'm guessing that's when I broke something.

---

