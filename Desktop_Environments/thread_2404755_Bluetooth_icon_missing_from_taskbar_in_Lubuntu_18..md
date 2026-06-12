---
title: "Bluetooth icon missing from taskbar in Lubuntu 18.04"
date: 2018-10-28
forum: Desktop Environments
---

### Post by nadrach on 2018-10-28
On a fresh install of Lubuntu 18.04 two quirks appeared on the taskbar.
I had two network icons, one attached to "indicator applets" and an extra one that appeared after I customized the display.
The extra one substituted for Bluetooth, in place before I customized.
Clicking on each of the two network icons displayed network data slightly differently.
A solution was to disable "Indicator Applications" in the Indicator applets configuration, leaving one network icon, but then I had no access to Bluetooth configuration.
The second network icon has recently disappeared in an update and I have Bluetooth configuration access back.
I have re-enabled Network configuration in "indicator applets".
What I don't have is a Bluetooth icon.
To access the Bluetooth configuration panel I hover the mouse over an apparently empty taskbar area until an outline of the space where the icon should be, shows up.
Any suggestions?

Later ...
Scrap that - still have two networking icons after a restart - and a blank Bluetooth space.
It seems that something recently reinstated my missing Bluetooth configuration access but left the duplicate networking icon in place. It's not part of indicator applets, because disabling "Indicator Applications" removes the first network configuration icon (again). Removing individual panel applets from the task bar setup does not remove the extra network configuration icon.
So I still have two quirks. An extra networking icon and a blank Bluetooth icon with no bluetooth symbol.
Any ideas as to what is happening here?

---

### Post by nadrach on 2018-11-08
OK, seems to partly be this bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1761606](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1761606)
Nomem Tuum Benedicamus

---

