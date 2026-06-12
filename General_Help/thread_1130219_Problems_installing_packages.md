---
title: "Problems installing packages"
date: 2009-04-19
forum: General Help
---

### Post by hemicro on 2009-04-19
I have just installed Ubuntu 8.10 and need to install ndisgtk package to enable my wireless adapter. The problem is after I mark for install and apply, it asks to install the disk labeled Ubuntu 8.10_Intrepid Ibex_ -Release i386 (20081029.5). When I load the cd and click ok nothing happens and I get an error message "w:failed to fetch cdrom:[Ubuntu 8.10_Intrepid Ibex_ -Release i386 (20081029.5)]/pool/main/n/ndiswrapper/ndiswrapper-common_1.52-1unbunt1_all.deb. The cdrom and contents show when I when access the drive thru "places". I'm pretty new to this and have no clue
hemicro

---

### Post by Titan8990 on 2009-04-19
System -> Administration -> Software Sources


Uncheck "cdrom" and apply the settings. Solved :D.

---

### Post by hemicro on 2009-04-19
If I uncheck the cdrom, the ndiswrapper packages are no longer available in the package list.

---

### Post by Titan8990 on 2009-04-19
Open up a terminal and copy and paste the following:


```
sudo apt-get update
```


Then look for ndiswrapper again.

---

### Post by hemicro on 2009-04-19
I don't have an internet connection yet, because I need ndiswrapper to enable the driver.

---

### Post by Titan8990 on 2009-04-19
Enable cdrom from the software sources menu as you had removed it earlier. Insert the cd and then proceed with installation of those packages off the cd.

---

### Post by hemicro on 2009-04-19
Thats where I run into the original problem. For some reason, the package is listed but when I try to install it, it asks to install the cd but doesn't seem to recognize or mount it.

---

### Post by Titan8990 on 2009-04-19
I should have read the first post more clearly. Mount the cdrom and post the output of:


find /media -name '*ndiswrapper*'

---

### Post by hemicro on 2009-04-19
I must be doing something wrong, because when I enter the line in terminal nothing happens. The cursor just goes to the next line.

---

### Post by Titan8990 on 2009-04-19
Does your cd spin up if its doing anything?

If the command returns nothing, that means it didn't find any ndiswrapper packages under the /media directory, where gnome-mount mounts drives.

---

### Post by hemicro on 2009-04-19
The cdrom doesn't sping up or seem to try
I have tried entering the command several ways
thinking I may have entered it wrong.

---

### Post by Titan8990 on 2009-04-19
Browse the CD via a gui or CLI, whichever you prefer and try to find the package its looking for: pool/main/n/ndiswrapper/ndiswrapper-common_1.52-1unbunt1_all.deb

---

### Post by hemicro on 2009-04-19
Don't know why, but I restarted the terminal and now the cdrom spun up and it found the ndiswrapper packages. What now?

---

### Post by Titan8990 on 2009-04-19
Copy and paste the output so I can see their exact location.

---

### Post by hemicro on 2009-04-19
Sorry it took so long, but I am on a different computer so I can't copy/pastel
/media/ubuntu 8.10/pool/main/n/ndiswrapper
/media/ubuntu 8.10/pool/main/n/ndiswrapper-common_1.52-1ubuntu_all.deb
/media/ubuntu 8.10/pool/main/n/ndiswrapper-utils-1.9_1.52-1ubuntu_i386.deb

---

### Post by hemicro on 2009-04-19
Thanks for your help. I went to the folder indicated by the "find" and opened the ndiswrapper folders with the "open with "gdebi package installer" and was able to install the 3 associated packages. I think that is how I will have to install the packages from the cdrom always.

---

### Post by Titan8990 on 2009-04-19
Good to hear you installed the needed packages. That is not how it is supposed to work but it functioned as a work-around.

---

