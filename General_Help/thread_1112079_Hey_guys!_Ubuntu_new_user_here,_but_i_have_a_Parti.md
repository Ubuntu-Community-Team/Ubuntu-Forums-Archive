---
title: "Hey guys! Ubuntu new user here, but i have a Partition Problem."
date: 2009-03-31
forum: General Help
---

### Post by Kikoshi on 2009-03-31
Hey guys! :) New guy here, Just installed Wubi for Windows, and well it installed and all, but then it gaved me a start up error. So i did the simple thing, I un-installed it and reinstalled ubuntu once more, but now I see 2 Ubuntu Names on windows boot where i get to choose what i want to boot from, anyway to know or how to remove one of them? Because I feel that i scrwed something up on the installation, which really makes no sense =/.

---

### Post by Kikoshi on 2009-03-31
Anyone?

---

### Post by kanikilu on 2009-03-31
A bump after 10 minutes? :rolleyes:

Anyways, you'll probably want to edit the boot.ini file from Windows:

[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

### Post by Kikoshi on 2009-03-31
> **kanikilu said:**
> A bump after 10 minutes? :rolleyes:

Anyways, you'll probably want to edit the boot.ini file from Windows:

[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)
Thanks for the quick reply, is just that i was scared i fked something up lol. 
Is this safe to do btw? Im running Window's Vista 64bit

---

### Post by Kikoshi on 2009-03-31
> **kanikilu said:**
> A bump after 10 minutes? :rolleyes:

Anyways, you'll probably want to edit the boot.ini file from Windows:

[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

Btw Kanikilu, If both Boot names are accesible and brings me to the same partition like the first one, Its safe to delete one of this entries in the boot.ini right?

---

### Post by kanikilu on 2009-03-31
> **Kikoshi said:**
> Btw Kanikilu, If both Boot names are accesible and brings me to the same partition like the first one, Its safe to delete one of this entries in the boot.ini right? I would think so. It's been a long time since I've edited that in Windows, but if there are 2 identical entries, I would assume it's safe to remove or comment one out.

---

### Post by Kikoshi on 2009-03-31
> **kanikilu said:**
> I would think so. It's been a long time since I've edited that in Windows, but if there are 2 identical entries, I would assume it's safe to remove or comment one out.
Awesome man! I did it but i used EasyBCD :D. IT was awesome! thanks for the fast reply bro!):P Now to enjoy this Wubi!

---

