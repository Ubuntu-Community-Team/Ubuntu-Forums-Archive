---
title: "What is generating console messages?"
date: 2010-12-16
forum: Desktop Environments
---

### Post by awp2513_ on 2010-12-16
Hi,

When I shut down or reboot I see output on the a console before the splash screen kicks in. An example:

```
Broadcast message from user@ubuntu
    (/dev/pts/0) at 6:24 ...

The system is going down for reboot NOW!
acpid: exiting

init: avahi-daemon main process (726) terminated with status 255
init: cron main process (808) killed by TERM signal
init: tty1 main process (1075) killed by TERM signal
modem-manager: Caught signal 16, shutting down...
init: Disconnected from system bus
```I have a few questions related to this output. 

1. The first is what is responsible for generating the output?

2. Am I even correct when I refer to these as "console messages"?

3. If I wanted to change the color of the text/background, what would I have to modify? I'm not even sure where this output is actually going (ttys are killed), so knowing that would help.

4. Is it possible to disable this output altogether (including the "broadcast message" portion of the output)? Commenting out "console output" in etc/init/rc.conf disabled all the output that used to follow the output above. Is there a way to modify /etc/init.d/sendsigs?

I'm trying to be specific as possible, but if I could provide more information or clarify something please let me know. Knowing the answers to 1 and 2 would probably help me ask 3 and 4 in a better way. 

Thanks in advance!

---

