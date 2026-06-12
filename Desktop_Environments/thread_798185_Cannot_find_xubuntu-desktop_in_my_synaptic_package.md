---
title: "Cannot find xubuntu-desktop in my synaptic package manager"
date: 2008-05-17
forum: Desktop Environments
---

### Post by enoughsaid05 on 2008-05-17
Just now I want to install xfce into my computer I couldn't find the package in the synaptic package manager. I tried xfce, xubuntu-desktop etc but to no avail.

Help! And thanks in advance!

BTW, I am using ubuntu hardy

---

### Post by NightwishFan on 2008-05-17
Check your software sources.

---

### Post by enoughsaid05 on 2008-05-18
I have checked the software sources and seems that every option has been checked.

---

### Post by NightwishFan on 2008-05-18
In a terminal type: ```
sudo apt-get update && sudo aptitude install xubuntu-desktop
```

Tell me if there is any error. It will likely say "cannot find package xubuntu-desktop" If that is the case choose another server to download from for the moment. There is an auto configuration under software sources.

---

### Post by TransitMan on 2008-05-18
It is located under Meta-Packages (Universal)

---

### Post by Cap'n Skyler on 2008-05-18
open synaptic and use the search feature.
and make sure you have not changed the selections for what repositories you will be using to do your installs/upgrades.
(open synaptic)
you can find those at synaptic
then settings
then repositories

---

### Post by enoughsaid05 on 2008-05-18
Tried using the command and it says couldn't find the package. I guess I may have to use another server. (But I was downloading from the main server, surely it should have...)

It is not under meta package either.

Ok, I have changed the server and finally finds xubuntu desktop.

Going to install it!

Thanks everyone and wish me luck! :P

---

### Post by NightwishFan on 2008-05-18
Of course, glad to be of help and good luck. :KS

---

