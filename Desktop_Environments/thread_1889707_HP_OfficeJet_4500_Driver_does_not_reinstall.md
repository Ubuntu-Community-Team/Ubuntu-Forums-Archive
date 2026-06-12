---
title: "HP OfficeJet 4500 Driver does not reinstall"
date: 2011-12-01
forum: Desktop Environments
---

### Post by helvecio on 2011-12-01
I had the HP OfficeJet 4500 Driver installed and working, including the scanner control. For some obscure reason (upgrade?) it stopped working and I decided to reinstall it. When I get to the end of the GUI part of the installation it loops back to the first GUI screen again, in an endless loop. The installation seems to go very smoothly, it sees the wireless printer, etc but there is the loop issue and the HPLIP program does not come up or sometimes it will come up but there will be no scan option.
I use Ubuntu 10.04, the driver I downloaded is the G510n-z.

---

### Post by DapperMe17 on 2011-12-01
Have you tried using the HP Toolbox GUI? 

You can find it in the repos under "hplip-gui". 

HP printers are well supported and it may help to solve your issues.

---

### Post by agillator on 2012-02-27
HPLIP is usually used for HP printers; I haven't found one yet that is unsupported. However, there seems to be something wrong with Ubuntu's installation of HPLIP, especially if you want to scan. See  [http://ubuntuforums.org/showthread.php?t=1898845](http://ubuntuforums.org/showthread.php?t=1898845) #9 for instructions on installing HPLIP. If you are setting it up for wireless access, follow the instructions as they are. If you are setting it up to be connected to the USB port, select that option in hp-setup when you get there instead of the network option. That should take care of your problem.

---

