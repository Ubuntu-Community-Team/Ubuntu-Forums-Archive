---
title: "Function Keys Don't work"
date: 2006-08-11
forum: Desktop Environments
---

### Post by tymanthius on 2006-08-11
A few weeks ago I noticed that I can no longer switch Virtural Terminals useing the ctrl+alt+FX key combo.

I did a search here, and found a few things, but nothing helped.

Yesterday, I also noticed that the F keys don't work in Midnight Commander.  This leads me to believe that something is hinky with the way Xubuntu is reading my keyboard.

To the best of my knowledge, nothing has changed.

Any thoughts?

---

### Post by der_joachim on 2006-08-11
Hmmm... What does your /etc/inittab say? Look for the following section:
```

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
#4:23:respawn:/sbin/getty 38400 tty4
#5:23:respawn:/sbin/getty 38400 tty5
#6:23:respawn:/sbin/getty 38400 tty6

```

I have three virtual terminals. The other three have been commented out. 

Another suggestion, probably useless: some Logitech keyboards have an F-lock key. When toggled, the F keys have their normal F function. Otherwiose, they are used as multimedia keys. Very irritating...

---

### Post by tymanthius on 2006-08-11
Good suggestion, but that's not it.  

As for the keyboard - I have a MS Natural Ergo 4000. And it has the same issue.  Thanks so much!  

I had never even noticed that key, b/c I don't use any of the special functions.

---

