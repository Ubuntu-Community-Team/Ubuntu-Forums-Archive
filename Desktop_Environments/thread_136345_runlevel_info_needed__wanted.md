---
title: "runlevel info needed / wanted"
date: 2006-02-25
forum: Desktop Environments
---

### Post by rfruth on 2006-02-25
My computer is working fine, just want to expand my horizons :) 
I have a stock /etc/inittab file (see below) runlevel 2 is my default (X, network, the whole 9 yards) so ctrl-alt-F1 gets me in single user mode as expected but its takes ctrl-alt-F7 to get back 2 runlevel 2 (I would expect F2 = runlevel 2 but no) why is this ?```

/etc/inittab: init(8) configuration.
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

```

---

### Post by Xian on 2006-02-25
Even though ctrl-alt-F1 gets you to single mode don't let that get you into the thinking that the system runlevels are associated in any way with the keyboard functions. What you have illustrated is just a coincidence.

---

### Post by taurus on 2006-02-25
Look further down in your /etc/inittab...

```

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

```

---

### Post by rfruth on 2006-02-26
I understand runlevels better now I really do thanks :)

---

### Post by vwiggin on 2006-02-28
Hi,

Good on you for hunting for information!

<ctrl>+<alt>+F1 buttons will change the virtual terminal to tty1, F2 -> tty2 up to F6 -> tty6, and like a post higher up mentioned, F7 usually takes you back to the graphic user interface.

virtual terminals and runlevels are not related, so changing to tty1 will not put you in single user mode, it just puts you in a text-terminal.

Runlevel has nothing to do with which virtual terminal you are in. Runlevel is a predetermined set of scripts that get run, where runlevel 0 kills all the programs and then halts the computer, runlevel 6 kills all the programs and then reboots the computer, and runlevels 1-5 do a combination of killing/starting (single or multi user, network or no, gui or no, etc, etc). These scripts can be seen in the /etc/rc#.d directories, where # is the runlevel number. The kill scripts start with a K and the start scripts start with an S.

\v

---

