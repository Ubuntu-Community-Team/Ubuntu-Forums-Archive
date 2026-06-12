---
title: "How to install newest version of Gnuplot?"
date: 2013-11-22
forum: Education &amp; Science
---

### Post by Vesnog on 2013-11-22
Hello everyone,

My aim is to install the latest version of Gnuplot which is version 4.6.4 on my computer running Ubuntu 12.04 LTS 32bit. I have downloaded the tarball, unpacked it and proceed as told in the readme files and the faq pdf included inside the package. However, when I try to launch Gnuplot from terminal the version 4.4 patchlevel 3 is executed. What can I do to prevent this and have the newest version launched? This may be related to my inexperience but I could not manage to execute the version 4.6.4 by any means. My goal is to have the newest version installed and launched all the time. Thanks in advance for your contribution, any suggestion is welcome.

---

### Post by Toz on 2013-11-22
An easier way, in lieu of building from source, is to use PPAs.

4.6.4 appears to be available in [this PPA]("https://launchpad.net/~gladky-anton/+archive/precise-backports"). 
Information on adding and using PPAs can be found [here]("https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_PPAs").

If you're looking for the absolute latest versions, [this individual]("https://launchpad.net/~matt-nycresistor/+archive/gnuplot") seems to build from CVS (currently 4.7 patchlevel 0).

---

