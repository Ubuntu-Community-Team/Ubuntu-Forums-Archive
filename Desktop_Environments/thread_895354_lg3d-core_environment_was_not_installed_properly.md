---
title: "lg3d-core environment was not installed properly"
date: 2008-08-20
forum: Desktop Environments
---

### Post by deep_90 on 2008-08-20
Hi

I tried to install lg3d-core 3D environment using apt-get (debian package).And while installation the package was not properly installed / configured.

The following was the error in post installation of lg3d-core configuration.


> 
pradheep@pradheep-desktop:~$ sudo apt-get install lg3d-core
[sudo] password for pradheep: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lg3d-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up lg3d-core (1.0.0) ...
/usr/share/lg3d/bin/../usr/share/lg3d/bin/postinstall: line 10: /bin/arch: No such file or directory
/usr/share/lg3d/bin/../usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: No such file or directory
Success. LG has been added as a gdm session.
/usr/share/lg3d/bin/../usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d-core
E: Sub-process /usr/bin/dpkg returned an error code (1)
pradheep@pradheep-desktop:~$ 


kindly help me in removing this package. And any other installations using apt-get is getting disabled due to this(lg3d-core) improper installation.

i tried the following commands to remove 

> sudo apt-get remove lg3d-core
> sudo apt-get purge lg3d-core
> sudo apt-get autoclean lg3d-core
> sudo aptitude remove lg3d-core 

All the above commands didnt remove the lg3d-core package completely.. kindly help

---

