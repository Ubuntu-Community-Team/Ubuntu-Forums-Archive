---
title: "amarok crashing - how to remove *all* amarok config files?"
date: 2006-03-30
forum: Desktop Environments
---

### Post by bionnaki on 2006-03-30
hello. for some reason or another, amarok has been crashing on me. I have sudo apt-get remove amarok (as well as "completely remove" in synaptic). After doing so and after reinstalling amarok, the app still crashes. I suspect it is a corrupted config file somewhere - the 1st error message tells me that a certain directory is not found (I recently deleted that directory before the crashing began). Because it is still looking for this directory, I know that some lingering configuration file is still somewhere in my system.

where are all the files for amarok located? I'd like to delete everything and reinstall. I have searched but could not find anything.

thanks!

---

### Post by aysiu on 2006-03-30
Try this.

Applications > Accessories > Terminal ```
killall amarok
rm -R ~/.kde/share/apps/amarok
sudo apt-get update
sudo apt-get install --reinstall amarok
amarok
```

---

### Post by jenred on 2006-03-30
To remove all package config files using apt try:

sudo apt-get --purge remove <package name>

---

