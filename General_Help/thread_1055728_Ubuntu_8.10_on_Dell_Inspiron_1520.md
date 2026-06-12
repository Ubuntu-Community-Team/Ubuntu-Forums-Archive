---
title: "Ubuntu 8.10 on Dell Inspiron 1520"
date: 2009-01-31
forum: General Help
---

### Post by STaylorY on 2009-01-31
Hey guys, I am interested in installing Ubuntu 8.10 on my Dell Inspiron 1520 but I have had some bad experiences with Linux distros in the past. Usually when I've tried to install a Linux distro some of my hardware would not be supported. Before I take the time to download the file I'd like for someone to tell me if they have succesfully installed Ubuntu 8.10 on their 1520 and got most if not all of the hardware to work.

My full system specs are:
-Dell Inspiron 1520
--Intel Core 2 Duo T730 (2.0GHz)
--Nvidia 8600M GT (256MB)
--2GB RAM
--and whatever the default sound and network cards were

Thanks,
-Taylor

---

### Post by mjpatey on 2009-01-31
I know Dell's 1525 is available preloaded with Ubuntu.  I don't know what hardware differences exist between the 1520 and 1525, so your results may vary... but the Dell site has an ISO of the latest Ubuntu customized for the 1525.  If it has a Live CD component, you may want to give that a shot!

Otherwise, just try burning a regular live CD of Ubuntu.  If it works and you're still gun-shy, you can install via WUBI, the Windows installer for Ubuntu, which allows Ubuntu to install without a separate partition on the system drive.  If you hate it, just boot into Windows and uninstall from Windows' standard "Add and remove programs" interface.

There's also a Dell-specific forum here on the Ubuntu Forums, I believe.  Click around a bit, and welcome to Ubuntu!

-Mark

---

### Post by minotauros on 2009-02-25
Ubuntu 8.10 works fine on my 1520. I have nearly the same specs as yours (higher processor) and so I will be surprised if it does not work for you...

However, if you are worried you can still install 8.10 using wubi [http://wubi-installer.org/](http://wubi-installer.org/)

This does not do a low level partition. Basically ubuntu is just a folder in windows (c:/ubuntu). For more info read in link above.

If you decide that all is good then you can do a full install (partition and so on)...

If you are unsure then while on win you go to the c:/ubuntu directory and you double click the un-install utility...

---

