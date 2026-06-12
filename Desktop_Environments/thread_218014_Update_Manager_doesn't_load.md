---
title: "Update Manager doesn't load"
date: 2006-07-18
forum: Desktop Environments
---

### Post by vishnu on 2006-07-18
When I receive an update notification and click it the update manager doesn't load. I see a progress bar downloading package info but then it disappears and is replaced with nothing.
I can load Update Manager via the System Menu and command line just not via the notifier.
Any ideas?

---

### Post by JerMe on 2006-07-18
Don't know what's going on with your Update-Manager, but at least you can use the terminal and the "apt-get" command to update via commandline.

Application > Accessories > Terminal

In Terminal, type "sudo apt-get update && sudo apt-get upgrade" (without the quotes).  Enter your password when prompted.

That'll essentially do what the update-manager was doing.

---

### Post by vishnu on 2006-07-18
It informs me that there are updates and I can load it from the System menu.  It's when I click the tray icon that notifies me of updates that it won't load.  Thanks for the command though - never knew that.

---

