---
title: "Synaptic/Update Manager Problem"
date: 2005-12-16
forum: Desktop Environments
---

### Post by Raoul Duke on 2005-12-16
Update Manager is showing some upgradeable packages (including Totem-xine 1.2.1 which I want because the current version is behaving badly), but does nothing when I click "Install" except to dim the window for a couple of secs. Synaptic shows no upgradeable packages at all (yes, I clicked on  "Reload"). Ideas anyone?

---

### Post by manicka on 2005-12-16
Try using Synaptic instead of the Update Manager and use the 'Mark all upgrades' button.

---

### Post by Raoul Duke on 2005-12-16
There are no upgrades to mark...tried anyway, no joy...

---

### Post by manicka on 2005-12-16
What happens if you click on 'apply' after 'Mark all upgrades'.

Try hitting 'Reload' as well.

if nothing is happening after all that, then you're system must be up to date.

Also, in a terminal you could try:

sudo apt-get update
sudo apt-get upgrade

This will do the same job as what you are trying to do with the update manager or synaptic.

---

### Post by Raoul Duke on 2005-12-16
OK, thanks, apt-get worked. I also re-installed update manager & synaptics to see if they get fixed, but won't know till there are more new packages.

---

### Post by manicka on 2005-12-16
Great :)

You could also try

```
sudo dpkg-reconfigure *package-name*
```

to reconfigure Synaptic and the Update Manager

---

