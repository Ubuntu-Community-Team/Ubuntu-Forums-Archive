---
title: "Wiimote Infra red tracking"
date: 2009-03-24
forum: Gaming &amp; Leisure
---

### Post by nathand28 on 2009-03-24
Following [these]("http://www.ubuntugeek.com/howto-get-wii-remote-working-in-ubuntu-810-intrepid-ibex.html") instructions, I managed to install it ok, and get the mouse to move when I tilt and twist the remote.
Whenever I try to run
```
gksudo wminput -c ir_ptr 00:22:4C:87:69:C8
```
I get this:
```
gksudo: invalid option -- 'c'
GKsu version 2.0.0

Usage: gksudo [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.
Etc etc
```
What would I need to change to get the command to work?

---

### Post by hikaricore on 2009-03-24
Something in your command there is mucking things up and gksudo is ignoring the wminput program completely.

I'm guessing it's the colons in your command, but I'm not sure.

Try running it with sudo instead of gksudo and see if it makes a difference.

---

