---
title: "offline packages"
date: 2005-10-27
forum: Desktop Environments
---

### Post by tosyu on 2005-10-27
Hey,

I've read some posts about downloading packages, burning them on a CD and using it as an offline repository, but something went wrong... :) 

All I did was browsing through the archive.ubuntulinux.org rep and downloading packages. When I wanted for example BeepMediaPlayer I opened the dsc file and checked for depends. Then I downloaded whole dir of the required package (like taglib). The same for all other packages. Next I executed dpkg-scanpackages .... etc. Then I burned it to a CD. I added it as a rep. But some packages aren't installing. Why? I have all the required files, but Synaptic complains... something like this "<package name> is not installable". WTF?

I will appreciate any help... :cry:

---

### Post by tonym on 2005-10-27
Try apt-get install package

At least this may give more detailed error messages.

---

