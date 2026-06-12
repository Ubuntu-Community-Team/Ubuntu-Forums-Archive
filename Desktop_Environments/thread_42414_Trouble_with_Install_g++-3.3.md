---
title: "Trouble with Install g++-3.3"
date: 2005-06-17
forum: Desktop Environments
---

### Post by vtechstu on 2005-06-17
Hey,

I'm trying to get Kompose installed, and it requires newer g++.  When I goto install it, i get this error:

[HTML]chase@ubuntu:~$ sudo dpkg -i g++-3.3_3.3.5-8ubuntu2_i386.deb
(Reading database ... 87775 files and directories currently installed.)
Preparing to replace g++-3.3 1:3.3.5-8ubuntu2 (using g++-3.3_3.3.5-8ubuntu2_i386.deb) ...
Unpacking replacement g++-3.3 ...
dpkg: dependency problems prevent configuration of g++-3.3:
 g++-3.3 depends on libstdc++5-3.3-dev (>= 1:3.3.5-8ubuntu2); however:
  Package libstdc++5-3.3-dev is not configured yet.
dpkg: error processing g++-3.3 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 chase@ubuntu:~$ sudo dpkg -i g++-3.3_3.3.5-8ubuntu2_i386.deb
(Reading database ... 87775 files and directories currently installed.)
Preparing to replace g++-3.3 1:3.3.5-8ubuntu2 (using g++-3.3_3.3.5-8ubuntu2_i386.deb) ...
Unpacking replacement g++-3.3 ...
dpkg: dependency problems prevent configuration of g++-3.3:
 g++-3.3 depends on libstdc++5-3.3-dev (>= 1:3.3.5-8ubuntu2); however:
  Package libstdc++5-3.3-dev is not configured yet.
dpkg: error processing g++-3.3 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 g++-3.3[/HTML] 

How do i configure this if it won't let me install it, and libstdc.  Thanks.

---

### Post by imightbegiant on 2005-06-17
Is there a reason you're not using synaptic to install kompose?

---

### Post by vtechstu on 2005-06-17
Yea, umm, retarded me, i didn't know kompose was in the universe files.  I fixed everything, thanks though.

---

