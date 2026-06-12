---
title: "Package not found!"
date: 2005-12-06
forum: Desktop Environments
---

### Post by Gordonbp531 on 2005-12-06
I installed the Kubuntu desktop on Ubuntu 5.10 using "apt-get install kubuntu-desktop" and everything was all OK.

can any one please tell me, why, when I do "apt-get remove kubuntu-desktop" it tells me that kubuntu-desktop is not installed (when it plainly IS) and I then have to go through all the kde packages in Synaptic to remove it?

---

### Post by GoldBuggie on 2005-12-06
It has to do with how apt-get works. kubuntu-desktop is a metapackage with refers to many packages which installes the kde desktop. But when uninstalling you need to uninstall every package manually. Every package is the same not only kubuntu-package. Install XXXX and it says you need this to(some dependencies). Ok no prob but when uninstalling it will leave your dependencies left on your computer.

There is a howto in the howto section about uninstalling kubuntu-desktop. Try that it will probably make things easier for ya.

---

### Post by Gordonbp531 on 2005-12-07
Thanks for that. A further question. is there an easy way of installing Kubuntu desktop WITHOUT Open Office 1.9? (I already have the Open office 2 Final installed.....)

---

### Post by aysiu on 2005-12-07
[QUOTE=gendibal]
can any one please tell me, why, when I do "apt-get remove kubuntu-desktop" it tells me that kubuntu-desktop is not installed (when it plainly IS) and I then have to go through all the kde packages in Synaptic to remove it?[/QUOTE] I wrote [a HowTo on removing the kubuntu-desktop package fully](http://www.ubuntuforums.org/showthread.php?t=96048).

---

### Post by aysiu on 2005-12-07
[QUOTE=gendibal]Thanks for that. A further question. is there an easy way of installing Kubuntu desktop WITHOUT Open Office 1.9? (I already have the Open office 2 Final installed.....)[/QUOTE] Sure. 

Open up Synaptic. 

Right-click on *kubuntu-desktop* and mark it for installation. 

Then, find OpenOffice 1.9, right-click it, and mark it not to be installed. 

Then Apply Changes.

---

