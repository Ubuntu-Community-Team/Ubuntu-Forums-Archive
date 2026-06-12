---
title: "Can't get VMWare to install or run. Please help."
date: 2006-08-26
forum: Desktop Environments
---

### Post by ebeyer on 2006-08-26
I'm running 6.06 on a Celeron-based system.

I installed VMWare player via the Add/Remove Programs tool.  This resulted in a script error, but the program appeared to be installed under System.  I ran it, attempting to launch the virtual machines for free SUSE and fedora core 5.  Both attempts gave me the error 'cannot find /dev/vmmon' and quit.  

So I tried completely removing the VMWare and the supporting kernel via Synaptic and tried installing VMWare player (and later, VMWare Server) by downloading the tarballs and extracting them to desktop; running the installer script.  But both attempts gave me an error, saying a previous version of VMWare was installed and aborted the installer. 

I am not sure where to go from here. I searched around for anything with 'vmw*' in it and came back with just the empty vmware player folder, which I deleted (to no effect).  I even created a new user and tried the install from there, but I got the same errors.

Any advice that can get me up and running would be really appreciated.

EB

---

### Post by Ziox on 2006-08-26
> **ebeyer said:**
> I'm running 6.06 on a Celeron-based system.

I installed VMWare player via the Add/Remove Programs tool.  This resulted in a script error, but the program appeared to be installed under System.  I ran it, attempting to launch the virtual machines for free SUSE and fedora core 5.  Both attempts gave me the error 'cannot find /dev/vmmon' and quit.  

So I tried completely removing the VMWare and the supporting kernel via Synaptic and tried installing VMWare player (and later, VMWare Server) by downloading the tarballs and extracting them to desktop; running the installer script.  But both attempts gave me an error, saying a previous version of VMWare was installed and aborted the installer. 

I am not sure where to go from here. I searched around for anything with 'vmw*' in it and came back with just the empty vmware player folder, which I deleted (to no effect).  I even created a new user and tried the install from there, but I got the same errors.

Any advice that can get me up and running would be really appreciated.

EB

go to synaptic and look to see if there are residul config file lying around...

---

### Post by Dubbayoo on 2006-08-26
try running **sudo vmware-config.pl** in an xterm.

---

