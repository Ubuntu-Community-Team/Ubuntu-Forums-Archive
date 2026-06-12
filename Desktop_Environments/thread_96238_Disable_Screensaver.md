---
title: "Disable Screensaver"
date: 2005-11-28
forum: Desktop Environments
---

### Post by markus79 on 2005-11-28
Love Ubuntu best distro I've ever tried as a newb. One quirk on my workstation though: when the screensaver goes off it completely crashes. I can't go to Preferences > Screensaver and turn it off there, becuase that crashes too. I think maybe its one of the default screensavers because as soon as it previews it crashes, so I have no time to stop it.

Is there a text file I can edit to turn it off, or another way then going thru Prefs?

Thanks
Markus

---

### Post by Xian on 2005-11-29
Try removing it completely and then doing a reinstallation.
That should set the config back to default.

$ sudo apt-get remove --purge xscreensaver

---

