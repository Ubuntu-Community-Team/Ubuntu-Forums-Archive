---
title: "bother with rpm"
date: 2006-10-07
forum: Desktop Environments
---

### Post by bluegroper on 2006-10-07
I gets this error 
```

root@thinkpad-t60:/home/user#rpm -Uvh VMware-workstation-5.5.1-19175.i386.rpm
error: Failed dependencies:
        /bin/sh is needed by VMwareWorkstation-5.5.1-19175.i386
```
/bin/sh exits and functions as a regular shell.
Any suggestions how to fix ?
TIA's
- BG

---

### Post by Markkreuzz on 2006-10-07
i don't get your point running an RPM package with Debian based ubuntu. RPM= Redhat Package Manager, which is used by a Redhat based distro. if you really want to install it, try running **alien** ```
sudo alien yourapp.rpm
``` and it will convert that package into a .DEB package which you can install using ```
sudo dpkg -i yourapp.deb
``` wich sometimes works. if does not then try looking for a .deb package for it. i havent used vmware before, so hope this works.:p

---

