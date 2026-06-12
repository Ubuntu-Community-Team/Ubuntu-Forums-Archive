---
title: "wubi - no wireless no ethernet - Acer Aspire One"
date: 2009-06-09
forum: General Help
---

### Post by aspergerian on 2009-06-09
I have installed Heron on Asus 901 and HP Mini 1000 Mi, using a Heron stick via instruction of Adam McDaniel [http://array.org/ubuntu/](http://array.org/ubuntu/)

A friend purchased an Acer Aspire One D250-1026, WalMart had only XP machines. Friend wants to run Ubuntu, but Acer has hidden bios on his Aspire One. I tried my Heron iso stick in each of the Acer's usb ports, but none is within the boot pathway. So friend loaded Wubi - and found that neither wireless nor ethernet is functional. Via XP, his Acer One connects either way, Atheros AR5007EG (wireless) or Atheros AR 8132 PC IE. 

Two threads seem relevant
[http://ubuntuforums.org/showthread.php?t=989819](http://ubuntuforums.org/showthread.php?t=989819)
which offers sudo modprobe ath_pci

and
[http://ubuntuforums.org/showthread.php?t=812855](http://ubuntuforums.org/showthread.php?t=812855)
which offers wicd, which is out of reach since the Aspire One won't connect to internet. 

I'll be meeting with friend later today. We'll try modprobe. Any other suggestions would be appreciated.

---

### Post by jzaragoza on 2009-06-10
Have you tried ndiswrapper? (wireless). For ethernet, I can't say.

---

### Post by pogztimz on 2009-06-10
> **aspergerian said:**
> I have installed Heron on Asus 901 and HP Mini 1000 Mi, using a Heron stick via instruction of Adam McDaniel [http://array.org/ubuntu/](http://array.org/ubuntu/)

A friend purchased an Acer Aspire One D250-1026, WalMart had only XP machines. Friend wants to run Ubuntu, but Acer has hidden bios on his Aspire One. I tried my Heron iso stick in each of the Acer's usb ports, but none is within the boot pathway. So friend loaded Wubi - and found that neither wireless nor ethernet is functional. Via XP, his Acer One connects either way, Atheros AR5007EG (wireless) or Atheros AR 8132 PC IE. 

Two threads seem relevant
[http://ubuntuforums.org/showthread.php?t=989819](http://ubuntuforums.org/showthread.php?t=989819)
which offers sudo modprobe ath_pci

and
[http://ubuntuforums.org/showthread.php?t=812855](http://ubuntuforums.org/showthread.php?t=812855)
which offers wicd, which is out of reach since the Aspire One won't connect to internet. 

I'll be meeting with friend later today. We'll try modprobe. Any other suggestions would be appreciated.

try this link. it might help. good luck..
[http://www.hp2133guide.com/forums/viewtopic.php?t=1507]("http://www.hp2133guide.com/forums/viewtopic.php?t=1507")

---

### Post by 3rdalbum on 2009-06-10
Use a later release. Intrepid has everything out-of-the-box except card reader (apparently it's meant to work?) and wireless (install the backport modules package and blacklist "ath_pci"). Jaunty even has wireless out-of-the-box, and I never tried the card reader.

ath_pci won't run the Aspire One's wireless. You need ath5k, which is what intrepid-backports-modules provides.

---

### Post by doccpu on 2009-06-13
its frustrating when some one says " just install, or just use this" when noone seems to tell you HOW to use or install same.

---

### Post by aspergerian on 2009-06-14
> **3rdalbum said:**
> Use a later release. Intrepid has everything out-of-the-box except card reader (apparently it's meant to work?) and wireless (install the backport modules package and blacklist "ath_pci"). Jaunty even has wireless out-of-the-box, and I never tried the card reader.

We succeeded to install 9.04 for Netbooks: 
[http://www.techdigest.tv/2009/04/how_to_install.html](http://www.techdigest.tv/2009/04/how_to_install.html)
[http://www.pendrivelinux.com/usb-ubuntu-netbook-remix-install/](http://www.pendrivelinux.com/usb-ubuntu-netbook-remix-install/)

Ken's Acer Aspire One then presented with the UNR desktop. A search for the traditional desktop via UNR led to a simple switch but also led to lots of problems induced by using that switch. 

As least is Aspire One is now functional, albeit with the UNR's clumsy desktop.

---

### Post by teh603 on 2009-06-14
You could just try using Jaunty regular, without UNR.

---

### Post by aspergerian on 2009-06-14
> **teh603 said:**
> You could just try using Jaunty regular, without UNR.

Ken is now downloading Gnome desktop. Perhaps that will be sufficient. If his Aspire One rebels, I still have the iso stick so that he can start over.

---

