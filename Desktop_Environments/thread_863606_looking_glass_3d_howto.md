---
title: "looking glass 3d howto"
date: 2008-07-18
forum: Desktop Environments
---

### Post by |{urse on 2008-07-18
this is just a cut and paste from the official lg3d site. I'm installing the latest nightly build, this wm looked really cool about a year ago.

 > Install using apt or the Synaptic Package Manager (on Ubuntu) by doing the following (you will need root permissions to do this, so sudo bash first) :

    * There are 3 LG3D repositories. The stable repository has the latest stable releases (0.8.1, 1.0 etc.). The testing repository has the pre-release builds (alpha, beta etc.) for the latest version and the unstable repsoitory has the nightly builds. To access these repositories, add the following lines to /etc/apt/sources.list and then comment/uncomment the appropriate line(s).

        	## LG3D repsoitories
        	deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib
        	# deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) testing contrib
        	# deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) unstable contrib
              

    * Then you can

                % apt-get update
        	  % apt-get install lg3d-core
              

---

### Post by thilinadg on 2008-07-24
I get this error when I try to install lg3d

++++-----
WARNING: The following packages cannot be authenticated!
  lg3d-jdk lg3d-java3d lg3d-core
Install these packages without verification [y/N]? y
Preconfiguring packages ...
Selecting previously deselected package lg3d-jdk.
(Reading database ... 132645 files and directories currently installed.)
Unpacking lg3d-jdk (from .../lg3d-jdk_1.6.0+b104_i386.deb) ...
Selecting previously deselected package lg3d-java3d.
Unpacking lg3d-java3d (from .../lg3d-java3d_1.5.0_i386.deb) ...
Selecting previously deselected package lg3d-core.
Unpacking lg3d-core (from .../lg3d-core_1.0.0_i386.deb) ...
Setting up lg3d-jdk (1.6.0+b104) ...

Setting up lg3d-java3d (1.5.0) ...

Setting up lg3d-core (1.0.0) ...
/usr/share/lg3d/bin/postinstall: line 10: /bin/arch: No such file or directory
/usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: No such file or directory
Success. LG has been added as a gdm session.
/usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d-core
E: Sub-process /usr/bin/dpkg returned an error code (1) 

-----++++


What should I do???

---

### Post by boterbram on 2008-12-13
Same error, any fixes?

---

### Post by |{urse on 2008-12-13
no, there arent unfortunately this is broken, and i upgraded to the most recent version and the version that worked is no longer linked and no fixes will be made it seems. bah!

---

