---
title: "Installation error"
date: 2006-07-25
forum: Desktop Environments
---

### Post by mozkaynak on 2006-07-25
Hi,
I have just tried to upgrade my Ubuntu to Drake. I did run update manager and tried to upgrade my system. While installation (after dowloading) the upgrade gave the following message:

Could not install 'linux-restricted-modules-common'

The upgrade aborts now. Please report this bug.

failed to write status record about `gnome-cups-manager' to `/var/lib/dpkg/status'


Can someone help me about this? What should I do right now? and will my current version of Ubuntu will be affected?
Thanks alot.

PS. I am relatively new to the Linux.

---

### Post by philippe_carlo on 2006-07-25
Can you maybe try the following:
```

sudo apt-get clean 
sudo apt-get update -f

```

---

### Post by mozkaynak on 2006-07-25
Thanks philippe_carlo.
I did run these commands.
then I got an error message related to dpkg. It was recommended to run 
sudo dpkg --configure -a. I did so. I worked fine.
should I run 
"sudo apt-get clean 
sudo apt-get update -f"
commands again?
could you also explain what is happening meanwhile. I am new to linux but I want to learn more and have a deeper understanding. Can us also recommend me some learning resources? 
Thanks for your time...

---

### Post by philippe_carlo on 2006-07-27
Basically, apt is the base package manager of the system (coming from debian). Other programs like aptitude or synaptic either run on top of it or provide similar features. They all use dpkg to actually install the programs. All that dpkg can do is check if all the necessary libraries are installed (the dependencies) and if not, it quits. It is apt that will take care of this by checking all the dependencies when you try to install a package. If the dependencies are not met, apt will download and install them from the repositories (in /etc/apt/sources.list). Sometimes, however, stuff goes wrong, e.g., offline repositories system crashes, disk full, ... Then dpkg is stopped in the middle of an installation. However, it still will require the installation to continue before any other programs are installed and this can be done with 'apt-get install -f'.

The best thing you can do if you want to know more about this is reading ubuntu howto's, man pages and searching the net. That hold for Linux in general.

---

