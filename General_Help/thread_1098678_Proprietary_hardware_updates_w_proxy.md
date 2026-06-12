---
title: "Proprietary hardware updates w/ proxy"
date: 2009-03-17
forum: General Help
---

### Post by adam35413 on 2009-03-17
I am trying to update my Nvidia driver behind a corporate firewall.  I have already set the environment variable for http_proxy and I was able to update everything using aptitude just fine.  However, when I go to the Hardware Drivers menu and try to upgrade, it fails and says it was unable to get the driver.  I have also setup the ftp proxy.

What else do I need to do to get this to work through the proxy?

---

### Post by adam35413 on 2009-03-17
I was able to download the drivers directly using wget and the installing them using dkpg.   However, I feel like there must be a better way of doing this.  Am I wrong?

---

### Post by taurus on 2009-03-17
Look in System -> Administration -> Synaptic Package Manager -> Settings -> Preferences -> Network.

---

### Post by adam35413 on 2009-03-17
I tried this at one point in my install process and it never helped.  I could definitely try it again however.

Edit:  I did and it worked this time.  Thanks for the help.

---

