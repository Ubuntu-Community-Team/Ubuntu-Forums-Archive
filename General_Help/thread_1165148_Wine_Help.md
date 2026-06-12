---
title: "Wine Help"
date: 2009-05-20
forum: General Help
---

### Post by sean hennington on 2009-05-20
I cannot get wine to load any windows programs correctly. I installed it useing the command "sudo apt-get install wine" what am i doing wrong....the programs usually load but they wont work properly

---

### Post by danwood76 on 2009-05-20
What programs are you trying to use?

The wine version in the repos is quite old compared to the latest one available from the winehq repos so it might be worth trying a later version.

---

### Post by sean hennington on 2009-05-20
ok, how do i try a new version...also i was trying to install windows as dual boot from an iso but it only loaded the welcome screen it wont install windows

---

### Post by danwood76 on 2009-05-20
wine wont allow you to install windows, you need to run a virtual machine to do that.

To get a later version of ubuntu go to the wine website: [http://www.winehq.org/](http://www.winehq.org/)
Follow the download link to ubuntu and add the repo and install.

---

### Post by XCan on 2009-05-20
> **sean hennington said:**
> ok, how do i try a new version...also i was trying to install windows as dual boot from an iso but it only loaded the welcome screen it wont install windows

Wait, are you trying to install Windows through Wine? I don't think that's a good idea. If you want a virtual machine for Windows running UNDER ubuntu I strongly suggest that you do it through Virtualbox.

---

