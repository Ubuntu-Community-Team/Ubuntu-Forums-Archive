---
title: "install package offline"
date: 2009-04-15
forum: General Help
---

### Post by zz701 on 2009-04-15
Hello,at the right time when a new system has been installed and when you want to download and install the first software or application ,the system will automatically download and install something that seems like 'packagelist":and i feel that no any other software or application can be installed until this 'packagelist" has been installed or upgrated.
  I want to know which place these things called as 'packagelist" will be downloaded to ,and how to back up or keep them so that when the next time install the ubuntu system ,i can **offline** install them and all other packages which have been downloaded.

---

### Post by SuperSonic4 on 2009-04-15
I think it will be somewhere in /var/apt/cache as deb files. If you do that beware of dependency hell

---

### Post by sedawk on 2009-04-15
There are two different procedures you might be looking for:

a) Generating a fresh installation media (e.g. DVD) where the master is
   the latest software on the internet or on your local computer.

b) Creating a local mirror that is used for local network installation
   (Really nice if your computer can even boot from network!)

I think there are detailed instructions for b) (debmirror?) 
but I'm not sure about a)

---

