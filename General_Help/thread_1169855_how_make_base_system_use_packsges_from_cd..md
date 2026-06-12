---
title: "how make base system use packsges from cd.?"
date: 2009-05-25
forum: General Help
---

### Post by agel1 on 2009-05-25
i want to install UBUNTU as minimal as possible using this guide [http://ubuntuforums.org/showthread.php?t=1155961&highlight=ubuntu+minimal+achieve](http://ubuntuforums.org/showthread.php?t=1155961&highlight=ubuntu+minimal+achieve) 

i can install the base system using the UBUNTU SERVER EDITION CD

but my problem is that the installation require lan internet to download the packages and my computer use wifi

i need to know if it is possible to make the base system use the packages from a UBUNTU CD, or put all the packages i need in a cd or dvd.?

THANKS

---

### Post by stefangr1 on 2009-05-25
The base system can be installed without internet. After installing, you have to edit your sources.list :

sudo nano /etc/apt/sources.list

and uncomment the deb cdrom entries. You have to put comments in from of the other repositories.

edit: another good option is always to install and configure the full system with the harddisk in another system, and than just move the disk to the system without ethernet.

---

### Post by agel1 on 2009-05-25
> **stefangr1 said:**
> The base system can be installed without internet. After installing, you have to edit your sources.list :

sudo nano /etc/apt/sources.list

and uncomment the deb cdrom entries. You have to put comments in from of the other repositories.

edit: another good option is always to install and configure the full system with the harddisk in another system, and than just move the disk to the system without ethernet.thanks i'm gona try it

---

### Post by agel1 on 2009-05-26
thank you stefangr1, did work

---

