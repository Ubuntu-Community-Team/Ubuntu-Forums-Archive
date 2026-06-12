---
title: "Very weird behavior in update-manager"
date: 2006-09-19
forum: Desktop Environments
---

### Post by twowheeler on 2006-09-19
I have been keeping my dapper system up to date with update-manager.  Today I got the little icon on my screen that says "There are 9 updates available."  Ok cool.  So I click on the icon and begin to look over the list before installing.  They are a new kernel linux-image-2.6.15-27-686, and new modules to go with it, plus some libgnutls stuff.  

Suddenly the screen goes black and scrambled with random graphics, then a plain full screen login terminal, then I am back to the gdm login screen.  So X and/or gnome evidently crashed and blanked the screen until gdm restarted.  I aint never seen that before!  This is repeatable behavior -- it occurs every time I click on the entry in update-manager for the aforementioned linux-image.  The text box shows "Downloading list of changes ..." for a moment, and then poof! it all disappears.

Anyone else seen this?  This system has been rock solid until this moment.  I don't if there is an error in the package or a bug in update-manager, but I am not installing this updated kernel until I know for sure.

---

### Post by hvbakel on 2006-09-20
try typing 'sudo apt-get update' on the command line, followed by 'sudo apt-get upgrade'. This will at least update all packages to the latest version.

---

### Post by Fire-Reiher on 2006-09-20
Seems to be a problem involving the nvidia-driver.
Here is the Malone bug entry:
[https://launchpad.net/products/update-manager/+bug/50054](https://launchpad.net/products/update-manager/+bug/50054)

---

### Post by twowheeler on 2006-09-21
Ok thanks.

---

