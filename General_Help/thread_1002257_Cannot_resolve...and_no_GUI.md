---
title: "Cannot resolve...and no GUI"
date: 2008-12-04
forum: General Help
---

### Post by penguinguy on 2008-12-04
I'm using Ubuntu 8.10 x64. When I boot to Ubuntu it sends me into one of those tty terminal things, like when you press Ctrl+Alt+F1. I can't switch to the graphical view.
When I try using aptitude or installing something with apt-get it says it could not resolve the software sources. I've tried some suggestions for sources.list that didn't work. All the deb and deb-src lines are uncommented.
I'm pretty sure this is related to me accidentally deleting Python earlier. Can anyone help me (I'm not too advanced with Linux yet)? ;) Thank you

---

### Post by abn91c on 2008-12-04
at the prompt make sure you can connect to your network, if you have broadband like cable internet type dhclient eth0, if you get a connection then do sudo apt-get update, then sudo apt-get upgrade
but you may have to do sudo dpkg --reconfigure -a first

---

### Post by EnGorDiaz on 2008-12-04
> **penguinguy said:**
> I'm using Ubuntu 8.10 x64. When I boot to Ubuntu it sends me into one of those tty terminal things, like when you press Ctrl+Alt+F1. I can't switch to the graphical view.
When I try using aptitude or installing something with apt-get it says it could not resolve the software sources. I've tried some suggestions for sources.list that didn't work. All the deb and deb-src lines are uncommented.
I'm pretty sure this is related to me accidentally deleting Python earlier. Can anyone help me (I'm not too advanced with Linux yet)? ;) Thank you

sudo apt-get install python 

otherwise reinstall ubuntu cus uninstalling python is one of the most rediculous things i have heard

---

### Post by penguinguy on 2008-12-05
Good thing I keep backups, because I end up screwing everything up at least once every other month. But it's fun screwing everything up.

I tried dhclient eth0, and it seemed to work, but anything sudo apt-get still cannot resolve the sources. Oh well, I'll probably reinstall it tomorrow or something.

---

### Post by abn91c on 2008-12-05
> **penguinguy said:**
> Good thing I keep backups, because I end up screwing everything up at least once every other month. But it's fun screwing everything up.

I tried dhclient eth0, and it seemed to work, but anything sudo apt-get still cannot resolve the sources. Oh well, I'll probably reinstall it tomorrow or something.

sorry for the earlier typo do at the prompt sudo dpkg --configure -a
then do sudo apt-get install -f

---

### Post by abn91c on 2008-12-05
by the way what's the prompt you get, is it like this user@ubuntu-desktop:~$ 
or is it something like  initramfs>

---

### Post by penguinguy on 2008-12-05
I figured out dpgk --configure -a, but sudo apt-get install -f gives this:
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded


Also, here's what happens when I try sudo apt-get install python:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main python2.5 2.5.2-11.1ubuntu1
Could not resolve 'us.archive.ubuntu.com'

Another similar 'us.archive.ubuntu.com' thing under that (sorry, I'm going off memory a bit here), 2 failed to fetch errors for the us.archive.ubuntu.com, and then:
E: Unable to fetch some archives, maybe try run -apt-get update or try with --fix-missing?
Those didn't work by the way.

Also, the prompt looks like user@user-desktop:~$

---

### Post by abn91c on 2008-12-05
run the command its suggesting, also if you have rebooted you will need to do dhclient  eth0 again then sudo apt-get check, if it sugest a command run it, then sudo apt-get update then sudo apt-get upgrade

---

### Post by abn91c on 2008-12-05
here is another command sequence i found in another post(run one at a time):
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean


then again you can try reinstalling the desktop sudo aptitude reinstall ubuntu-desktop

---

