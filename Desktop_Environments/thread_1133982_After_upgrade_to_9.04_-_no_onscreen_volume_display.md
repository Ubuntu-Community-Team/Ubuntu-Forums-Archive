---
title: "After upgrade to 9.04 - no onscreen volume display"
date: 2009-04-23
forum: Desktop Environments
---

### Post by steinrr on 2009-04-23
I have an IBM Thinkpad Z61m with dedicated buttons for volume up/down and mute. In Ubuntu 8.10 an onscreen display showed up when using these buttons. In Ubuntu 9.04, no onscreen display for volume pops up when using thse, but the buttons still works ok.

Any ideas?

---

### Post by andrewabc on 2009-04-23
9.04 uses new notification system
notify-osd

Make sure that is installed.
Search through [Jaunty development board](http://ubuntuforums.org/forumdisplay.php?f=352) as others have had similar problems.

search that part of forum for "notify"
Example:
[http://ubuntuforums.org/showthread.php?t=1111228](http://ubuntuforums.org/showthread.php?t=1111228)

---

### Post by steinrr on 2009-04-24
Thanx! Found this bug report:

[https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/357673](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/357673)

Fabio: notification were originally working because each time you pressed a key, it was handled both through hardware and software, which meant that it was as if you had pressed the key twice. To correct that problem, software handling of those keys was removed for the ThinkPads. However, because the notifications were handled by the software handler, a side effect of this was that notifications were lost. What really needs to be done is to enable notification on hardware events.

---

