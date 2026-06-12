---
title: "aptoncd unable to mount"
date: 2009-03-02
forum: General Help
---

### Post by kask1984 on 2009-03-02
hi every body. i want to use aptoncd method to install softwares on a system which is not connected to internet. my friend system has net connection and he installed all required softwares   by downloading from net.i created a cd using aptoncd.in my system i added that cd as third party software in software sources.but, when i put that cd in my system ,system is showing unable to mount cd and i am unable to install any softwares.

i followed another method also i.e., copying " /var/cache/apt/archives " files to pendrive from my friend system and giving corresponding commands in my system but this method is failed to install, showing u have some broken packages.

my aim is to install softwares offline(without internet) .

please give me suggestions 
 i am and my friend using ubuntu 8.10 .

thanks

---

### Post by zvacet on 2009-03-02
> this method is failed to install, showing u have some broken packages

```
sudo apt-get -f install
```

or 

```
sudo dpkg --configure -a
```

should take care of broken packages.

---

### Post by kask1984 on 2009-03-02
i tried u r commands but those are not working.
the broken packages were removed but new softwares were not installed

---

### Post by kask1984 on 2009-03-02
i tried u r commands but those are not working.
the broken packages were removed but new softwares were not installed
please give me suggestion

---

### Post by zvacet on 2009-03-02
If your packages are in var/cache/apt/archives then go to the synaptic and click on mark all update button (or something similar;I don´t use English version)and your pasckages should be installed.

---

