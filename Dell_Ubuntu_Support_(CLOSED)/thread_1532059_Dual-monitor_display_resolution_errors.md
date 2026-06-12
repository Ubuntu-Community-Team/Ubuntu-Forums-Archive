---
title: "Dual-monitor display resolution errors"
date: 2010-07-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rjgarner on 2010-07-15
I'm using a Dell E6400 laptop, with an E-port plus port replicator and dual E248WFP 24" monitors.  The display is configured to use Twinview with both monitors in 1920x1080 mode.  The video card is an nvidia Quadro NVS 160M.  I'm using the nvidia driver, and X is configured using the nvidia-settings utility.  It's Ubuntu Lucid/10.04, pretty vanilla install.

It's been running without problems until last week sometime, when I noticed a flickering row of pixels along the right-hand edge of the left-hand screen.  The on-screen display of the monitor says that the monitor is running at 1922x1080 resolution, 2 pixels wider than its maximum resolution.  Occasionally the monitor blanks out, complaining that the requested resolution is higher than it supports, but it comes back after a few seconds.

The resolution occasionally changes to 1924x1080 or 1926x1080.

I've tried using a couple of different versions of the nvidia driver: the old version from the Ubuntu repository (173.14.22) as well as the current (185.something) and the latest version from the nvidia website (256.35) - no change.  But I don't think it's driver related because it started happening with no accompanying change in drivers.

The only vaguely relevant reference I can find by googling is this discussion from the Radeon IRC channel

[http://www.radeonhd.org/?page=archive_display&c=radeon&m=4&y=2010&d=2010-4-19](http://www.radeonhd.org/?page=archive_display&c=radeon&m=4&y=2010&d=2010-4-19)


It's probably related to one of the Ubuntu software updates from last week (I generally apply them as they arrive).

Help!

Robin Garner
Southern Cross University

---

### Post by rjgarner on 2010-07-18
Solved.  Turns out to be a dodgy cable.

---

