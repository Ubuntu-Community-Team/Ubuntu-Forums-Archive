---
title: "Remove or prevent gdm from starting."
date: 2012-08-26
forum: Desktop Environments
---

### Post by nickajeglin on 2012-08-26
I just upgraded to pangolin. I originally installed xubuntu on a small netbook, but I now only use it as an ssh server for a variety of things. Because I never use the desktop environment, I would like to either remove it, or prevent it from starting. I suppose I better keep something lightweignt like blackbox just in case, but as of now I'm manually stopping gdm every reboot, which is getting old.

In summary: how do I get rid of the xubuntu desktop (I think it's xfce)and replace it with something more lightweight? And how do I prevent the desktop environment from running on boot?

---

### Post by nab on 2012-08-26
Hi Nick,

The most debian way would be deinstall gdm, if you don't need it:
$ sudo apt-get --purge remove gdm

Niko

---

### Post by ajgreeny on 2012-08-26
Are you sure it is gdm that you are using in Xubuntu 12.04?  The default now is lightdm, but if you updated you may still have gdm.  Either way you can edit the /etc/init/lightdm.conf (or gdm.conf) and comment out the section shown in red below.
```
# LightDM - light Display Manager
#
# The display manager service manages the X servers running on the
# system, providing login and auto-login services
#
# based on gdm upstart script

description    "LightDM Display Manager"
author        "Robert Ancell <robert.ancell@canonical.com>"

[COLOR=Red]# start on ((filesystem
#           and runlevel [!06]
#           and started dbus
#           and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
#                or stopped udev-fallback-graphics))
#         or runlevel PREVLEVEL=S)[/COLOR]
```There is a similar section in the gdn.conf file which you can comment out, if gdm is what you are using.

---

### Post by nickajeglin on 2012-08-26
I did just notice that gdm has been replaced by lightdm. That conf is exactly what I needed. It is better I think to simply keep lightdm from starting, rather than take the rather extreme step of removing it. This way I can manually start it if I need to. Thank you all for your help.

---

