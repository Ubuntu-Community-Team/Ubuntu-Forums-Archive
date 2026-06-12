---
title: "Ubuntu 14.04 - Icons missing from system tray"
date: 2015-07-17
forum: Desktop Environments
---

### Post by luvshines on 2015-07-17
I have been using Ubuntu 14.04 with Unity.

And the issue I am facing is that multiple apps which used to appear in the system tray are now missing. It's not that all of them are missing, just few of them, generally the ones which are my work related(office) apps.
The log files for those apps show successfully running, but they don't appear in the system tray
I don't have command line to change the parameters for those apps so am stalled at this moment.

Any help would be greatly appreciated. Where to look for issues, debug etc ?

---

### Post by dino99 on 2015-07-18
[http://askubuntu.com/questions/456950/system-tray-icons-disappeared-after-installing-ubuntu-14-04](http://askubuntu.com/questions/456950/system-tray-icons-disappeared-after-installing-ubuntu-14-04)
glance at the 9th comment, it explain the change made; so some apps still need to follow the new design

---

### Post by luvshines on 2015-07-28
Thanks for the reply.
I have already installed libappindicator1 and libappindicator3-1, but no avail.
The icons are still missing for most of my office apps

---

### Post by luvshines on 2015-07-31
!! Bump !!

---

### Post by mc4man on 2015-08-02
It can be re-enabled in the unity source but you may find this indicator much easier to implement. Can be configured to some extent - see
[http://ubuntuforums.org/showthread.php?t=2280775&p=13297076&viewfull=1#post13297076](http://ubuntuforums.org/showthread.php?t=2280775&p=13297076&viewfull=1#post13297076)

---

### Post by luvshines on 2015-08-03
Nice !!
Thanks, that solved it :guitar:

---

