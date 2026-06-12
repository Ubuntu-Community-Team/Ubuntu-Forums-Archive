---
title: "Virtual Terminal Ctrl+Alt+F2 doesn't' work!"
date: 2009-06-29
forum: Desktop Environments
---

### Post by android73 on 2009-06-29
Can anyone assist me on why I am simply getting a blinking cursor and nothing else when I hit this on my keyboard? I assume you are supposed to see a blank screen and then asked for your root password? Thanks in advance for any help!

---

### Post by Greyfox_75 on 2009-06-29
Does Ctrl+Alt+F3 work?  Did you boot into single user mode?

Virtual terminals are created with files in /etc/event.d/ do you have a file in that folder called tty2?  It should contain

```
# tty2 - getty
#
# This service maintains a getty on tty2 from the point the system is
# started until it is shut down again.

start on runlevel 2
start on runlevel 3

stop on runlevel 0
stop on runlevel 1
stop on runlevel 4
stop on runlevel 5
stop on runlevel 6

respawn
exec /sbin/getty 38400 tty2
```

---

### Post by android73 on 2009-06-30
Hi, thanks for the reply! Yep, my tty2 file is exactly as you describe. Hmmm??? Could this be a nvidia graphics display problem or something?

---

### Post by Greyfox_75 on 2009-07-06
Try going to the grub menu to edit the kernel load options, and take off quiet splash.  This might give you a better idea of what is holding up your system.

---

