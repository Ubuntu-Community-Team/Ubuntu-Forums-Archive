---
title: "constant error while updating or installing programs"
date: 2009-03-20
forum: General Help
---

### Post by mdinh on 2009-03-20
i am running ubuntu 8.10 and ever since i installed ubuntu onto my compaq laptop ive been getting the same error whenever i download or update anything. the message i get is "Sorry, the package "system-tools-backends 2.6.0-1ubuntu1.1" failed to install or upgrade"

can anyone please give me VERY detailed instructions on how to fix the system-tools-backends problems. im a beginner with linux so i need step by step instructions on what to type in the terminal and everything else

thanks to everyone in advance

---

### Post by cariboo on 2009-03-20
I found this work around on [launchpad]("http://bugs.launchpad.net/ubuntu/intrepid/+source/system-tools-backends/+bug/294389"):

> ***TEMPORARY WORKAROUND***
After the upgrade has failed, you will get an error every time you run dpkg or apt-get saying that system-tools-backends is not configured. "sudo dpkg --configure -a" will not fix this. To recover, please perform the following 2 steps:

1) sudo invoke-rc.d system-tools-backends stop
2) sudo dpkg --configure -a

this works...

Apparently the bug is fixed in Juanty

---

### Post by Therion on 2009-03-20
Open a Terminal and then Copy and Paste the following commands one at a time:```
sudo invoke-rc.d system-tools-backends stop
sudo dpkg --configure -a
```

---

