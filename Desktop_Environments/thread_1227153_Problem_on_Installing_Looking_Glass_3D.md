---
title: "Problem on Installing Looking Glass 3D"
date: 2009-07-30
forum: Desktop Environments
---

### Post by bm.riyadh on 2009-07-30
Hi,

                                 I have downloaded   and installed lg3d_jdk1.6.0_i686.deb,  lg3d_java3d_1.5.0_i686.deb and  lg3d-core_1.0.0_i686.deb (JRE 6 already installed).  After installing I have got a lots of errors. By searching in this forum I got this solution:
 

 “$ cd /bin
$ sudo gedit
- This opens the text editor -

In the text editor:
add the following line:

uname -s

 

 This solves the problem partially and reduced number of errors. Now when I reinstall lg3d-core, I get this error message
 

 “Preparing to replace lg3d-core 1.0.0 (using lg3d-core_1.0.0_i686.deb) ...
Success. LG has been removed as a gdm session.
Unpacking replacement lg3d-core ...
Setting up lg3d-jdk (1.6.0+b104) ...

Setting up lg3d-java3d (1.5.0) ...

Setting up lg3d-core (1.0.0) ...
Success. LG has been added as a gdm session.
/usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../lib/linux-Linux/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d-core"

 What should I do? I am using Ubuntu 9.04. Please HELP!!!

---

