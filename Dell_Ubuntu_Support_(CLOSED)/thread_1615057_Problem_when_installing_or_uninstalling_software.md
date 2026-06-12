---
title: "Problem when installing or uninstalling software"
date: 2010-11-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by FreddyStrauss on 2010-11-06
Hello, I'm new to Ubuntu. I installed the last 64b ubuntu release  to date ( November 3. 2010) My computer is a Dell 1545  notebook. Everything was working pretty fine with the exception of this problem i'm going to describe.
Whenever I want to install or uninstall new software using the Ubuntu Software center or by the update manager I get the following message (link to an screenshot of what i get): 

[http://imagebin.org/122062](http://imagebin.org/122062)

Which contains the following message:

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 143702 files and directories currently installed.) 
Removing gnome-sudoku ... 
Processing triggers for python-support ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for man-db ... 
Processing triggers for python-support ... 
Setting up firmware-b43-installer (4.150.10.5-4) ... 
Not supported low-power chip with PCI id 14e4:4315! 
Aborting. 
dpkg: error processing firmware-b43-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Setting up firmware-b43-installer (4.150.10.5-4) ... 
Not supported low-power chip with PCI id 14e4:4315! 
Aborting. 
dpkg: error processing firmware-b43-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 

Is there some way to fix this? although the message appears, the software seems to get installed or uninstalled whenever i require the action, it is just the error message that i get, but i'd be pleased to get a message according to the successful operation.

Thank you in advance

Freddy Strauss

---

### Post by sikander3786 on 2010-11-06
Hi.

Try from terminal

```
sudo apt-get install --reinstall firmware-b43-installer
```

If it gives some errors, try

```
sudo apt-get remove --purge firmware-b43-installer
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

Please post the output of each command seperately.

---

### Post by FreddyStrauss on 2010-11-06
Fixed it thanx to a friend that told me to write this on Terminal:

sudo apt-get remove firmware-b43-installer

THe problem no longer exists.

---

### Post by FreddyStrauss on 2010-11-06
Thanks!

---

