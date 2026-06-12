---
title: "how to install programs to pc doesn't have internet connection"
date: 2011-11-14
forum: Desktop Environments
---

### Post by forsubhi on 2011-11-14
how to install vlc without any internet connection in ubuntu 11.10?
how to install flash player without any internet connection in ubuntu 11.10?
and so many other programs

---

### Post by Frogs Hair on 2011-11-14
Take a look at the link . There was a script for previous versions of Ubuntu specifically  for installing the restricted extras including flash and VLC  offline , but I find no current version the most recent  was for 10.04 .  
 [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by cortman on 2011-11-14
Real simple.

Open up Synaptics on the offline PC.

Right click on the programs you want to install (they'll be listed) and select "mark for installation".

Click "File" and select "Generate package download script"

Save the script on a USB flash drive.

Go to a computer that has an internet connection. Make a folder for the packages in /home and copy/paste the script file "*.sh" into the folder.

Run the script. This will download the packages required.

Copy them onto the flash drive and then onto the offline PC.

Open Synaptics, select 'File/Add downloaded packages' and select the packages.

That should work! It's been a real handy way for me to get programs since I don't have internet at home or close by.

---

### Post by forsubhi on 2011-11-18
thank you very much I'll try the second approach

---

