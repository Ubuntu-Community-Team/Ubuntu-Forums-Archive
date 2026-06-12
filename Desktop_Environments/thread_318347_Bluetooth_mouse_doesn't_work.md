---
title: "Bluetooth mouse doesn't work"
date: 2006-12-13
forum: Desktop Environments
---

### Post by furriner on 2006-12-13
There has been much wailing for years that people's Bluetooth mice do not work with ubuntu. My Microsoft Bluetooth mouse does not work with Edgy Eft unless you issue an

tadeusz@media:~$ hidd --connect 00:50:F2:E7:C3:D2
Can't get device information: Host is down

If I try

tadeusz@media:~$ sudo hidd --search
Password:
Searching ...
        Connecting to dev ce 00:50:F2:E7:C3:D2
tadeusz@media:~$ 


then the mouse starts to work.

What do I have to do to get my MS BT mouse working without having to click buttons on the mouse each time and issue a command?

---

