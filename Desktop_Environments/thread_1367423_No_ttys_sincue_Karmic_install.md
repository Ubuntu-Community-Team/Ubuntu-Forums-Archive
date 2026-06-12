---
title: "No ttys sincue Karmic install"
date: 2009-12-29
forum: Desktop Environments
---

### Post by reedk on 2009-12-29
I did a fresh install of 9.10, and I've noticed that the ttys normally reachable with ctrl+alt+F[1-6] are "gone." By gone, I see a blinking underline cursor but no login. Also, I've noticed that X is now associated to the tty on F1, rather than the F7 it's been on for longer than I can remember. Is this a new "feature," or should I expect alternate ttys?

---

### Post by zerocc on 2010-01-04
My fresh install came with following files, which are obviously missing from your system:

*/etc/init/tty1.conf* through to */etc/init/tty6.conf*

which follow this formatL

[I]# tty6 - getty
#
# This service maintains a getty on tty6 from the point the system is
# started until it is shut down again.

start on runlevel [23]
stop on runlevel [!23]

respawn
exec /sbin/getty -8 38400 tty6
[/I]
which you obviously adapt to each tty number.

The x-session appears to default to lowest available F-key, which is logical.

---

