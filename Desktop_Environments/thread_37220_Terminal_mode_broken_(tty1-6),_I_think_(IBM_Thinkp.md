---
title: "Terminal mode broken (tty1-6), I think? (IBM Thinkpad)"
date: 2005-05-26
forum: Desktop Environments
---

### Post by Sleeper Service on 2005-05-26
I've got a very strange problem.  When I jump into terminal mode by pressing Ctrl+Alt+[f1-f6] I just get a block of colour (or many colours) and no text.

It's intermittent, though.  It only happens once I've logged in through the graphical display once or twice.

Related to this, the system rarely powers off properly, because when gdm stops, there's just this screen frozen with colour, instead of the shutting-down terminal output.  So system shut down happens - but power off doesn't happen, presumeably because of the frozen screen.

I can live with the lack of automatic power-off, but having no terminal mode is a really serious problem for me.

 :?

[ps] btw, I'm using Ubuntu 5.04 on an laptop (IBM Thinkpad T21).

---

### Post by rtz654 on 2005-05-27
please post your entries in /etc/inittab, there your consoles are defined!

---

### Post by Sleeper Service on 2005-05-31
**@rtz654:** I've appended the contents of /etc/inittab (sorry about the length).

I've also clarified the point at which "terminal mode" "breaks".  It's when I log out of a window manager AND gdm is running underneath.  It doesn't happen if gdm is not running, or if, instead of logging out, I execute ```
/etc/init.d/gdm restart
```

Anyway, here's /etc/inittab:

```

# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:wait:/sbin/sulogin

# /etc/init.d executes the S and K scripts upon change
# of runlevel.
#
# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.

l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6
# Normally not reached, but fallthrough in case of emergency.
z6:6:respawn:/sbin/sulogin

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now

# Action on special keypress (ALT-UpArrow).
#kb::kbrequest:/bin/echo "Keyboard Request--edit /etc/inittab to let this work."

# What to do when the power fails/returns.
pf::powerwait:/etc/init.d/powerfail start
pn::powerfailnow:/etc/init.d/powerfail now
po::powerokwait:/etc/init.d/powerfail stop

# /sbin/getty invocations for the runlevels.
#
# The "id" field MUST be the same as the last
# characters of the device (after "tty").
#
# Format:
#  <id>:<runlevels>:<action>:<process>
#
# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

# Example how to put a getty on a serial line (for a terminal)
#
#T0:23:respawn:/sbin/getty -L ttyS0 9600 vt100
#T1:23:respawn:/sbin/getty -L ttyS1 9600 vt100

# Example how to put a getty on a modem line.
#
#T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3

```

---

