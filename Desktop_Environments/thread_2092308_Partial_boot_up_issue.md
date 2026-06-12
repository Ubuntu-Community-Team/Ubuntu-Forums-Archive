---
title: "Partial boot up issue"
date: 2012-12-07
forum: Desktop Environments
---

### Post by archangel2003 on 2012-12-07
I already have an issue where it takes a long time to boot Ubuntu, but now when I start it up, it either stays on the purple screen after the password is input, or my desktop picture shows up, but it's like a photograph, and none of my folders or the tool bars show up.

Nothing but the mouse works, and it only moves, nothing else.

It would be like a blank screen if not for the background picture.

I then have to kill the power and start over.

Most of the time the second go around works, sometimes it's the third or fourth before it works right.

---

### Post by Kirk Schnable on 2012-12-07
It may be worth your time to use another TTY to look at what's going on during this time. Commands like top, iotop, etc might come in handy. Top can look at running processes, CPU usage, etc, and iotop can show you disk utilization by process. 

You can access another TTY by pressing CTRL+ALT+F1. Login there, and run the commands you want to get information. 

You should be able to switch back to your graphical session by hitting either CTRL+ALT+F7 or CTRL+ALT+F8 at any time.

---

