---
title: "Window manager suddenly doesn't start automatically"
date: 2005-11-11
forum: Desktop Environments
---

### Post by Gordonbp531 on 2005-11-11
Suddenly my machine only boots to the command line: how do I get the Windows Manager to start automatically again? (I don't ming typing "startx" at the log-in prompt - my other users won't want to do that....)

Thanks

---

### Post by Gordonbp531 on 2005-11-11
I'll re-phrase that - what happens is that the log-in screen suddenly doesn't appear.

---

### Post by vruum on 2005-11-11
are you getting any error messages? if not, try typing this in a terminal, and post the output here:
```

cat /etc/inittab

```
also, when you've logged in on the prompt, try, instead of typing startx, typing 
```

sudo /etc/init.d/gdm start

```
just to make sure gdm (the graphical login) is working

---

### Post by Gordonbp531 on 2005-11-11
Result of cat /etc/inittab:

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

---

### Post by Gordonbp531 on 2005-11-11
The result of "sudo /etc/init.d/gdm start" is nothing! Just back to the command line log-in prompt.

---

### Post by vruum on 2005-11-11
that's a bit odd, try reinstalling gdm, either through synaptic, or with:
```

sudo apt-get install --reinstall gdm

```

---

### Post by Gordonbp531 on 2005-11-11
Sorted - interestingly it would seem that the installation yesterday of gnome-audio is what borked the gdm!  Strange or what?

Many thanks for the assistance.

---

### Post by vruum on 2005-11-11
Heh, yeah, it seems to conflict with ubuntu-audio, on which gdm depends, and ubuntu-desktop depends on, both I guess, so it's not as innocent as it looks

---

