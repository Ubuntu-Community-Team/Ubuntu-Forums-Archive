---
title: "No screensaver available in 10.04?"
date: 2012-02-07
forum: Desktop Environments
---

### Post by fxer on 2012-02-07
Using a server install of Ubuntu 10.04 with a later added '--no-install-recommends ubuntu-desktop' which apparently doesn't install the screensaver control? Also the software center has no screensaver packages available, gnome-screensaver nor xscreensaver

Any idea how to get the screensaver (ultimately to enforce a password reprompt after x mins)?

---

### Post by Krytarik on 2012-02-07
You know, it's kinda weird that you know of the "--no-install-recommends" option (for the command line, obviously) but insist on using the Software Center to install packages which's exact names you apparently also know (but yes, both packages don't turn up in my USC either, weirdly, Lucid 10.04 too).

So, to install "[gnome-screensaver]("http://packages.ubuntu.com/lucid/gnome-screensaver")" with recommends:
```
sudo apt-get install gnome-screensaver
```And without recommends:
```
sudo apt-get install --no-install-recommends gnome-screensaver
```Regards.

---

