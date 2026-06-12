---
title: "Install KDE4 standalone for testing in VM"
date: 2007-09-07
forum: Desktop Environments
---

### Post by miggols99 on 2007-09-07
I am testing out KDE4, and would like to keep an up to date version in a VM. How would I go about doing this? I'd rather not have KDE3 apps available for me to use when I have a perfectly fine KDE here.

---

### Post by maybeway36 on 2007-09-07
Install VirtualBox ([virtualbox.org]("http://www.virtualbox.org")) from either innotek's repos or the deb package. Then go about installing Kubuntu. (Don't forget to install Guest Additions, it makes it that much better)

---

### Post by miggols99 on 2007-09-08
I am just wondering if I can get a cleaner VM without having to install KDE3...maybe I could install openSUSE or Mandriva,  as it says on the KDE website that they also have KDE4 packages. What do you recommend?

---

### Post by kugn on 2007-09-08
How about running KDE 4 in xterm? there are instructions [here]("http://kubuntu.org/announcements/kde4-beta2.php") that tells you how to do so. you wouldn't have to install any KDE3 stuff

---

### Post by maybeway36 on 2007-09-08
Use the Ubuntu or Kubuntu alternate CD, install a command-line system, then enable backports:
```
sudo nano /etc/apt/sources.list
```
Then install the xorg package and kdebase-workspace. (Also you might want kdm, gdm, xdm or wdm.)
Your ~/.xsession should read:
```
#!/bin/sh
export LD_LIBRARY_PATH=/usr/lib/kde4/lib
export KDEDIRS=/usr/lib/kde4
export PATH=/usr/lib/kde4/bin/:$PATH
export KDEHOME=~/.kde4
startkde
```

---

### Post by miggols99 on 2007-09-23
The KDE4 in openSUSE doesn't work too well...are there any distros that provide svn packages for KDE4? Kubuntu just provides beta 2, which doesn't really work at all...please help. I really want to try a decently working KDE4 like in those screenshots....

---

