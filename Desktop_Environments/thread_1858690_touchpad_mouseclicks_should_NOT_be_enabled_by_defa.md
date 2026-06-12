---
title: "touchpad mouseclicks should NOT be enabled by default!"
date: 2011-10-12
forum: Desktop Environments
---

### Post by Furcifer on 2011-10-12
In fact, touchpad mouse-clicks should be against international and maritime law, and punishable by death.  

One particular bane of any Network Admin's existence (besides printer cartridge supply logistics) on Windows LANs is top-level shared folders being accidentally drug into other folders, destroying links and impacting the entire organization.  Fat-fingered inadvertent clicks are bad enough, but I'd rather see the ladies' room toilet seats be tap-to-click enabled on the network than touchpads by default.  If somebody wants to enable this PIA on their own machines, fine and dandy.  THEY should be the ones who have to go in and change it - at THEIR OWN risk.

---

### Post by Copper Bezel on 2011-10-12
A good cautionary story. It wouldn't make any sense to disable a core functionality of a device explicitly designed for a given purpose, but if the Mouse settings aren't giving you enough control, try gpointing-device-settings.

Edit: I'm not certain how you might set these values as default, but since this has posed a problem in the past, certainly let the employees know to make the change themselves.

Edit: Or, simpler, run this:

```
gconftool-2 --type bool --set /desktop/gnome/peripherals/touchpad/tap_to_click "false"
```

Edit again: I found [_a bit for setting defaults system-wide_]("http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/4/html/Desktop_Deployment_Guide/s1-ddg-intro-gconf-default-mandatory.html") in Red Hat this way, but it's not working for me in Ubuntu, I think because the user permissions are handled differently.

Edit the Third: And finally the right answer, straight from _[the Wiki page on using Ubuntu in corporate environments]("https://help.ubuntu.com/community/CorporateUbuntu")_.

```
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type bool --set /desktop/gnome/peripherals/touchpad/tap_to_click "false"
```

Run that command on each new machine, and tap-to-click can never be enabled by any non-root user.

---

