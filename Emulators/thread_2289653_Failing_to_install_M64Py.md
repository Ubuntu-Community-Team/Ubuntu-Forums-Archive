---
title: "Failing to install M64Py"
date: 2015-08-05
forum: Emulators
---

### Post by ellie4 on 2015-08-05
I'm trying to install M64Py for Mupen64Plus, but this is the result: 

&#10140;  ~  sudo apt-get install M64Py   Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 m64py : Depends: python3-pyqt5.qtopengl but it is not going to be installed
         Depends: python3-pyqt5.qtsvg but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
&#10140;  ~ 
Upon trying to install python3-pyqt5.qtopengl...

&#10140;  ~  sudo apt-get install python3-pyqt5.qtopengl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
 python3-pyqt5.qtopengl : Depends: python3-pyqt5 (= 5.2.1+dfsg-1ubuntu1) but 5.3.1-1 is to be installed
E: Unable to correct problems, you have held broken packages.
&#10140;  ~ 
What can i do to resolve this?

---

### Post by deadflowr on 2015-08-06
Where are you installing it from?
As it does not exist within the default Ubuntu repository system...

If you added a 3rd party repo, like playdeb or getdeb.
You might need to run a full system update.
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
In order of each command.
The update command will refresh the system's list of available packages.
The upgrade command will safely update any package that now has a new package available, but only if the upgraded packages will not require the installation or removal of any other packages.
The dist-upgrade command will ignore the safety net imposed by the upgrade command and install any and all packages, regardless of whether they will install or remove other packages.
(though it's probably a little more complex than that, that's the basic gist of it)

I have no idea if this will help, but if it does good.
If it doesn't, then post the output for the three commands to see if something else is needed...

---

