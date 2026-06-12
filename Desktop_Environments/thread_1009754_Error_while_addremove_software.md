---
title: "Error while add/remove software"
date: 2008-12-13
forum: Desktop Environments
---

### Post by ramesh20033 on 2008-12-13
Hi,

I installed ubuntu 8.04.1 desktop in my computer.Though i had downloaded an iso image and copied it to a cd,when i tried to install inside windows xp,it started downloading and it took nearly 12 hours of installation.After completing the installation i had around 202 upgrades which took another 8 hours.Now whenever i am trying to install using add/remove options i am getting an error which says E:dprg was interrupted,you must manually run "dprg --configure -a" to correct problem.E:_cache->open()failed.please report.Can somebody guide me how to correct this problem.I am new to ubuntu.Please give me step by step advice.Also how to get a backup copy of ubuntu in case i require it in future,as it is painful and time consuming to instal through net.
Thanks in advance.

---

### Post by ugm6hr on 2008-12-13
It took 12 hours to install from a CD?  Did you check that there were no errors on the CD?  Even the slowest computer should not take 12 hours to install from a CD.

Anyway - just follow the advice given (with the addition of sudo):
```
sudo dpkg --configure -a
```

In order to save having to download all updates again, keep a backup of all the .deb files in /apt/cache/archives.  You can then copy them back there (using sudo) following a reinstallation, and it will find them (therefore, bypassing need to download again).

---

### Post by ramesh20033 on 2008-12-13
Thanks a lot ugm6hr,

I got it sorted as per your guidance.I have installed ubuntu 8.10 in my new laptop from a torrent downloaded cd which got installed without any problem.When i installed ubuntu8.04 in my 5 years old desktop,i had the above problem.I had downloaded ubuntu 8.04 through torrents twice and i have 2 cds which are vof no use.Any how thanks a lot for your guidance.

---

