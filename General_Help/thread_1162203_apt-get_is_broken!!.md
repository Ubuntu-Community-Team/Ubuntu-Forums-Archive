---
title: "apt-get is broken!!"
date: 2009-05-17
forum: General Help
---

### Post by erixoltan on 2009-05-17
When I try to run Synaptic Package Manager, it immediately exits with the following error message.```
E: The package ghostscript needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```So then I try to remove and reinstall ghostscript to fix the problem manually.```
ildi@ildi-xubuntu:~$ sudo apt-get remove ghostscript
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ghostscript needs to be reinstalled, but I can't find an archive for it.
ildi@ildi-xubuntu:~$
```This is a Xubuntu Intrepid system.  It's my Mom's laptop so I'd prefer to fix it rather than having to reformat and reinstall from scratch.  

But I'm pretty much dead in the water.  Does anyone know a good workaround?

---

### Post by geirha on 2009-05-17
What does it output if you attempt to reinstall it?
```
sudo aptitude update
sudo aptitude reinstall ghostscript
```

---

### Post by erixoltan on 2009-05-17
HOLY MOLEY IT WORKED!!

Thanks for your help.  I can get updates again now.  I'm not sure why I didn't think to use update first, I could've sworn I had tried that.  

Erik

---

