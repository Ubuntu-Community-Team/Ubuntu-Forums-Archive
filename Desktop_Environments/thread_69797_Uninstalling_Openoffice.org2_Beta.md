---
title: "Uninstalling Openoffice.org2 Beta"
date: 2005-09-27
forum: Desktop Environments
---

### Post by banjobacon on 2005-09-27
I installed OOo2 beta following the instructions found [here](https://wiki.ubuntu.com/OpenOffice2Beta?highlight=%28openoffice%29). How do I go about uninstalling it now? Removing the packages installed via Synaptics does not get rid of the programs.

---

### Post by RikoW on 2005-09-28
Since the script you mentioned converts the OOo rpms to debs and then installs them via dpkg, you should be able to uninstall OOo2beta with Synaptic.

Open Synaptic and search for "openoffice" and remove the all packages with version number 1.9.* (whatever beta you have install).

Good luck,

               Riko

---

### Post by manicka on 2005-09-28
Synaptic doesn't remove the package properly because the script moves the folder that the programs are in, after it is installed. After removing it with synaptic then go the /opt folder and remove any of the openoffice1.9 folders that you find there.

---

### Post by bdamon on 2005-09-28
Here is what I did.

sudo apt-get remove openoffice*


You can use the -s option to see what it is going to remove first.

I then installed the most recent beta release.
This seemed to work ok for me on a couple of machines.

---

