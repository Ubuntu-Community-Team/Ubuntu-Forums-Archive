---
title: "Changes to Panels Revert After Reboot."
date: 2012-07-04
forum: Desktop Environments
---

### Post by jbrice on 2012-07-04
This is an Xubuntu 12.04 desktop PC with encrypted Home and Swap folders. 
Adding or changing order of launchers in a panel reverts to the previous setting after a reboot, but not after a panel restart (xfce4-panel --restart).
Config. file permissions look fine, so would appreciate any suggestions as to where else to look.

TIA

---

### Post by Merrattic on 2012-07-04
So if after changes you restart the panel then reboot, does it stick?

This smacks of a permissions issue, but I could be wrong. How are you set up user wise?

---

### Post by jbrice on 2012-07-04
> So if after changes you restart the panel then reboot, does it stick?

No - unfortunately not.

> This smacks of a permissions issue, but I could be wrong. How are you set up user wise?

Er - fairly conventionally. My log-in is the user generated on installation, with sudo powers if necessary.

---

### Post by Merrattic on 2012-07-05
May be something to do with your xfce-session? Try ticking / unticking some checkboxes in Settings > Session & Startup: e.g. General > Save session on logout, or Session > Save Session.

You can also "watch" the xml files in /etc/xdg/xfce4/xfconf/panel
& /etc/xdg/xfce4/xfconf/xfce-perchannel-xml

to see what, if anything, happens when you make changes?

---

### Post by jbrice on 2012-07-07
General > Save session on logout, or Session > Save Session has no effect on this.
However the tip to watch the files is a good one. I had assumed that they only got updated on shutdown, so had been tediously restarting to check if the changes had stuck.
However the config files change whenever a panel parameter is altered, and knowing this and which files are affected madit it much easier to trouble-shoot.
In the end it seems to have been a permissions problem, although I thought I had that angle covered. But changed all relevant permissions to match aN Xubutnu system that was OK in this respect, and all is now good.

Thanks!

---

