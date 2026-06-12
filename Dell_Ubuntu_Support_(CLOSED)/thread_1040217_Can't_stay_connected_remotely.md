---
title: "Can't stay connected remotely"
date: 2009-01-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by euclidsbrother on 2009-01-15
Have a Dell XPS m1710 laptop with the broadcom wireless a/b/g/n adapter.  All works fine when sitting in front of it.. Using the Broadcom STA driver.

The problem is when connecting to it remotely, either with SSH or VNC (or even connecting to a virtualbox vm windows guest with LogMeIn).  It will connect fine, but anywhere froma few seconds to 30 seconds later it will disconnect.  VNC client is the only one that gives an actual error message (ReadExact: Socket error while reading.)  The Wireless icon in the tool bar says 100% signal strength.

I don't have any problem staying connected to any of my other machines using LogMeIn or Radmin (the rest are all windows).  And when this laptop is booted to Vista, there's never any problem staying connected over the wireless connection.

I think tommorrow i'll leave it connected with the wire instead of wireless and see if the problem still exists.

Has anyone else had a similar issue?  Man, I realy like ubuntu, I finally got everything setup the way I want.  But, sadly, not being able to stay connected remotely is gonna be a deal breaker.. :(

Thanks,
-EB

Edit: when it disconnects, I can immediately reconnect w/o any problems.. but it just keeps disconnecting..

---

### Post by euclidsbrother on 2009-01-15
well.. it may be due to the VBox Vista Guest..  I'm noticing so far that it only has a problem while it's running.  Don't know yet if it's a direct conflict with that, or a side effect (like too much cpu usage causing the disconnect).  But with the VM not running, i was connected for about an hour.

Also seems to happen with VBox XP guest running.. Alot of problems staying connected while it's booting, but once it booted, then seems somewhat stable.. but still disconnects after a minute or so..

---

### Post by euclidsbrother on 2009-01-15
well.. so much for that idea.. vnc's disconnecting every few seconds now.. with nothing running but conky.

---

