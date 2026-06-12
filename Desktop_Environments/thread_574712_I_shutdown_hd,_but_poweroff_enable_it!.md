---
title: "I shutdown hd, but poweroff enable it!"
date: 2007-10-13
forum: Desktop Environments
---

### Post by gaiterin on 2007-10-13
I use an usb linux in my laptop sometimes.
I sleep the internal hd with: 
hdparm -Y /dev/sda

but when I poweroff (slax 5), a daemon enables the internal hd and shutdown inmediaty. It do a "tick" sound in the hd. I read that is bad [https://bugs.launchpad.net/linux/+bug/67810](https://bugs.launchpad.net/linux/+bug/67810)

How can I disable the daemon that restarts the hd?
Thanks!

---

### Post by gaiterin on 2007-10-17
The solution :)
Boot with Slax 6 ([www.slax.com](www.slax.com)).
in the directory /root/.kde/Autostart create a script shutdown.sh with the command:
hdparm -y /dev/sda
;)

---

