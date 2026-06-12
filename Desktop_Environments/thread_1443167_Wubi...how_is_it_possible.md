---
title: "Wubi...how is it possible?"
date: 2010-03-30
forum: Desktop Environments
---

### Post by Granny_Geek on 2010-03-30
I have Ubuntu 9.10 installed using Wubi. I am quite curious as to HOW it works...how is Wubi different from say VirtualBox, etc? How is it possible? I tried searching but that was leading me to how to install a distro using Wubi. Any input would be appreciated, perhaps you know of a web site with that info. Thanks GG

---

### Post by lovinglinux on 2010-03-30
Wubi is not exactly a virtual machine, is more like a virtual drive, since it can't be executed within the host.

---

### Post by ssulaco on 2010-03-30
From Wubi FAQ's.........[http://wubi-installer.org/](http://wubi-installer.org/)
> 
How does Wubi work?

Wubi adds an entry to the Windows boot menu which allows you to run Linux. Ubuntu is installed within a file in the Windows file system (c:\ubuntu\disks\root.disk), this file is seen by Linux as a real hard disk.

Is this running Ubuntu within a virtual environment or something similar?
No. This is a real installation, the only difference is that Ubuntu is installed within a file as opposed to being installed within its own partition. Thus we spare you the trouble of creating a free partition for Ubuntu. And we spare you the trouble to have of having to burn a CD-Rom.


also....[http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer)](http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer)))

---

### Post by Granny_Geek on 2010-03-30
Thanks to ssulaco & lovinglinux for taking the time to stop by and giving me a little more understanding about how Wubi works:)

---

