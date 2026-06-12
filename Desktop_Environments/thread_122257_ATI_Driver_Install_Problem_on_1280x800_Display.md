---
title: "ATI Driver Install Problem on 1280x800 Display"
date: 2006-01-27
forum: Desktop Environments
---

### Post by lkdhiri on 2006-01-27
Hi,

I have previously tried to install earlier versions of the ATI drivers for my Samsung's PCIE X300 graphics system but I've always have the same problem. The installer starts fine and I choose customised driver for distro after this the selection box is so large it does not fit on screen so I simply can't make a choice. Has anyone else had this problem? I have contacted ATI support but they have refused to help me saying it's Samsung's responsibility:confused: 

TIA

---

### Post by homerhomer on 2006-01-27
yep, I had the same thing.  Command line is the key

this page helps out a lot [http://ubuntuforums.org/showthread.php?p=423584#post423584](http://ubuntuforums.org/showthread.php?p=423584#post423584)

this command will build the driver that you want 
sudo sh ./ati-driver-installer-8.21.7-i386.run --buildpkg Ubuntu/breezy
[http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/)

I used the info from the first link but used the drivers from the following link and everything worked well
[http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/)

---

### Post by lkdhiri on 2006-01-27
Thanks for your help. I followed the instructions on link and managed to compile and install the drivers. Brilliant!

What I can't find is how to set the colour depth to 16 bit. Do I just manualy edit the xorg.conf file?

I will try to look into this more when I get back from work.

Thanks

---

