---
title: "Switching from Ubuntu to Kubuntu...how?"
date: 2010-05-10
forum: Desktop Environments
---

### Post by InfectionZero on 2010-05-10
Hello All, 
Complete noob here... how do I switch from Ubuntu 10.04 to the KDE environment? Is there a simple step to enable this interface? I thought I read it somewhere but can't find the thread anymore. Thanks all.

---

### Post by ronnielsen1 on 2010-05-10
should be as simple as installing kubuntu-desktop in synaptic or sudo apt-get install kubuntu-desktop in a terminal. You could choose de's in login or remove ubuntu-desktop

---

### Post by ronnielsen1 on 2010-05-10
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by 3Miro on 2010-05-10
> **InfectionZero said:**
> Hello All, 
Complete noob here... how do I switch from Ubuntu 10.04 to the KDE environment? Is there a simple step to enable this interface? I thought I read it somewhere but can't find the thread anymore. Thanks all.

From the terminal (Apps -> Accessories -> Terminal) type:
```
sudo apt-get install kubuntu-desktop
```

This will ask for password, then download about 700MB of files and install them. Then you need to logout and select that you want to use KDE session, then log back in.

(another option would be to install Kubuntu from scratch, but it takes longer and involves formating partitions and such)

---

